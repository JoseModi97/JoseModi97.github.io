---
title: Yii Essentials
description: A blog post on how I used query builder to perform advanced searched
author: modi
date: 2024-09-02 12:05:00 +0800
categories: [Yiiframework, Essentials]
tags: [php]
pin: true
math: true
mermaid: true
---

## Create Raw Sql from Yii2 $dataProvider
```php
$dataProvider->query->createCommand()->getRawSql()
```


## Sample Kartik GridView

```php
use kartik\grid\GridView;
<?= GridView::widget([
    'dataProvider' => $dataProvider,
    'showPageSummary' => true,
    'headerRowOptions' => ['class' => 'kartik-sheet-style grid-header'],
    'filterRowOptions' => ['class' => 'kartik-sheet-style grid-header'],
    'pjax' => false,
    'responsiveWrap' => false,
    'condensed' => true,
    'hover' => true,
    'striped' => false,
    'bordered' => false,
        'columns' => [
            [
            'class' => 'kartik\grid\SerialColumn',
            'contentOptions' => ['class' => 'kartik-sheet-style'],
            'width' => '36px',
            'pageSummary' => '<b>TOTALS</b>',
            'pageSummaryOptions' => ['colspan' => 3, 'class' => 'text-bold'],
            'header' => '',
            'headerOptions' => ['class' => 'kartik-sheet-style text-bold'],
            'width' => '4%',
            ],
            [
            'attribute' => 'unit_code',
            'header' => '<b>UNIT</b>',
            'vAlign' => 'center',
            'hAlign' => 'left',
            'width' => '10%%',
            ],
            [
            'attribute' => 'unit_name',
            'header' => '<b>UNIT NAME</b>',
            'vAlign' => 'center',
            'hAlign' => 'left',
            ],
            [
            'header' => strtoupper('<b>Male</b>'),
            'value' => function ($model) {
                    return $model['male_count'];
            },
            'format' => 'raw',
            'pageSummary' => true,
                    'vAlign' => 'center',
                    'hAlign' => 'center',
            ],
            [
            'header' => strtoupper('<b>FEMALE</b>'),
                    'value' => function ($model) {
                        return $model['female_count'];
                    },
            'format' => 'raw',
            'pageSummary' => true,
            'vAlign' => 'center',
                    'hAlign' => 'center',
            ],
            [
            'header' => strtoupper('<b>TOTAL</b>'),
            'value' => function ($model) {
                    return $model['student_count'];
            },
            'pageSummary' => true,
            'pageSummaryOptions' => ['class' => 'text-bold'],
            'vAlign' => 'center',
            'hAlign' => 'center',
            ],
            ],
            'panel' => [
                'heading' => 'Sample Panel Heading'
            ],
            'showFooter' => true,
            'export' => ['fontAwesome' => true],
            'exportConfig' => [
                    'pdf' => [
                    'filename' => Yii::$app->formatter->asDatetime(time(), 'yyyy-MM-dd HH:mm:ss'),
                    'label' => 'PDF',
                    'showConfirmAlert' => false,
                    'config' => [
                        'methods' => [
                                'SetHeader' => [$header],
                                'SetFooter' => ['{PAGENO}'],
                        ],
                        'contentBefore' => $contentBefore,
                        'format' => 'A4-P',
                            'cssInline' => '
                                    body { 
                                        font-family: "Cambria"; 
                                        font-size: 8pt; 
                                        color: #000000; 
                                        }
                                    .header, .footer { 
                                        font-family: "Cambria"; 
                                        font-size: 8pt; 
                                        color: #000000; 
                                        }
                                        a{
                                        text-decoration: none;
                                        color:black;
                                        }
                                        .card-footer{
                                        display: none;
                                        }
                                        .kv-panel-after{
                                        display: none
                                        }
                                        .kv-table-footer{
                                        display: none
                                        }
                                        ',
                                    'contentAfter' => '',
                                    'options' => [
                                        'title' => 'My Customized PDF Export',
                                        'subject' => 'My Subject',
                                        'keywords' => 'My Keywords',
                                    ],
                                ],
                            ],
                        ],
                    ]); ?>
```




## Controller Example

```php
<?php

namespace app\modules\courseRegistration\models\search;

use app\models\CrProgCurrTimetable;
use yii\base\Model;
use yii\data\ActiveDataProvider;
use Yii;
use yii\db\Expression;
use yii\db\Query;

/**
 * CoursesRegisteredSearch represents the model behind the search form of `app\modules\feesManagement\models\AcademicProgress`.
 */
class CoursesRegisteredSearch extends CrProgCurrTimetable
{

    public
        $semster_name,
        $programme_level_name,
        $study_group_name,
        $prog_full_name,
        $prog_code,
        $acad_session_name,
        $academic_level_name,
        $acad_session_id,
        $semester_code,
        $prog_short_name,
        $course_name,
        $semester_type,
        $student_number,
        $surname,
        $other_names,
        $course_code,
        $course_reg_type_name,
        $unit_name;
    /**
     * {@inheritdoc}
     */
    public function rules()
    {
        return [
            [['programme_level_name', 'unit_name', 'course_code', 'course_reg_type_name', 'other_names', 'surname', 'student_number', 'semester_type', 'study_group_name', 'semster_name', 'prog_full_name', 'prog_short_name', 'course_name', 'prog_code'], 'safe'],
            [['acad_session_id', 'acad_session_name', 'academic_level_name', 'semester_code'], 'required']
        ];
    }

    /**
     * {@inheritdoc}
     */
    public function scenarios()
    {
        // bypass scenarios() implementation in the parent class
        return Model::scenarios();
    }

    /**
     * Creates data provider instance with search query applied
     *
     * @param array $params
     *
     * @return ActiveDataProvider
     */
    public function search($params)
    {
        $searchParams = Yii::$app->request->get('CoursesRegisteredSearch', []);
        $query = (new Query())
            ->select([
                'smis.org_courses.course_id',
                'smis.org_courses.course_code',
                'smis.org_courses.course_name',
                'smis.cr_course_reg_type.course_reg_type_code',
                'smis.cr_course_reg_type.course_reg_type_name',
            ])
            ->from('smis.cr_course_registration')
            ->innerJoin('smis.cr_prog_curr_timetable', 'smis.cr_course_registration.timetable_id = smis.cr_prog_curr_timetable.timetable_id')
            ->innerJoin('smis.org_prog_curr_semester_group', 'smis.cr_prog_curr_timetable.prog_curriculum_sem_group_id = smis.org_prog_curr_semester_group.prog_curriculum_sem_group_id')
            ->innerJoin('smis.org_prog_curr_semester', 'smis.org_prog_curr_semester_group.prog_curriculum_semester_id = smis.org_prog_curr_semester.prog_curriculum_semester_id')
            ->leftJoin('smis.org_prog_level', 'smis.org_prog_curr_semester_group.programme_level = smis.org_prog_level.programme_level_id')
            ->innerJoin('smis.org_programme_curriculum', 'smis.org_prog_curr_semester.prog_curriculum_id = smis.org_programme_curriculum.prog_curriculum_id')
            ->innerJoin('smis.org_prog_curr_unit', 'smis.org_programme_curriculum.prog_curriculum_id = smis.org_prog_curr_unit.prog_curriculum_id')
            ->innerJoin('smis.org_unit_history', 'smis.org_prog_curr_unit.org_unit_history_id = smis.org_unit_history.org_unit_history_id')
            ->innerJoin('smis.org_unit', 'smis.org_unit_history.org_unit_id = smis.org_unit.unit_id')
            ->innerJoin('smis.org_programmes', 'smis.org_programme_curriculum.prog_id = smis.org_programmes.prog_id')
            ->innerJoin('smis.org_academic_session_semester', 'smis.org_prog_curr_semester.acad_session_semester_id = smis.org_academic_session_semester.acad_session_semester_id')
            ->innerJoin('smis.org_semester_code', 'smis.org_semester_code.semester_code = smis.org_academic_session_semester.semester_code')
            ->innerJoin('smis.org_academic_session', 'smis.org_academic_session_semester.acad_session_id = smis.org_academic_session.acad_session_id')
            ->innerJoin('smis.org_prog_curr_course', 'smis.cr_prog_curr_timetable.prog_curriculum_course_id = smis.org_prog_curr_course.prog_curriculum_course_id')
            ->innerJoin('smis.org_courses', 'smis.org_prog_curr_course.course_id = smis.org_courses.course_id')
            ->innerJoin('smis.cr_course_reg_type', 'smis.cr_course_registration.course_registration_type_id = smis.cr_course_reg_type.course_reg_type_id')
            ->innerJoin('smis.org_semester_type', 'smis.org_prog_curr_semester.semester_type_id = smis.org_semester_type.semester_type_id')
            ->innerJoin('smis.org_study_centre_group', 'smis.org_prog_curr_semester_group.study_centre_group_id = smis.org_study_centre_group.study_centre_group_id')
            ->innerJoin('smis.org_study_centre', 'smis.org_study_centre_group.study_centre_id = smis.org_study_centre.study_centre_id')
            ->innerJoin('smis.org_study_group', 'smis.org_study_centre_group.study_group_id = smis.org_study_group.study_group_id')
            ->innerJoin('smis.sm_student', 'smis.cr_course_registration.registration_number = smis.sm_student.student_number')
            ->where([
                'smis.org_programmes.prog_id' => Yii::$app->request->get('prog_id'),
                'smis.org_academic_session.acad_session_id' => Yii::$app->request->get('acad_session_id'),
                'smis.org_prog_level.programme_level_name' => Yii::$app->request->get('programme_level_name'),
                'smis.org_semester_code.semster_name' => Yii::$app->request->get('semster_name'),
                'smis.org_study_group.study_group_name' => Yii::$app->request->get('study_group_name'),
                'smis.org_semester_type.semester_type' => Yii::$app->request->get('semester_type'),
                'smis.sm_student.student_id' => Yii::$app->request->get('student_id'),
                'smis.org_unit.unit_id' => Yii::$app->request->get('unit_id')
            ]);
        if (!empty($searchParams)) {
            $course_code = $params['CoursesRegisteredSearch']['course_code'] ?? '';
            $course_reg_type_name = $params['CoursesRegisteredSearch']['course_reg_type_name'] ?? '';

            $query->andFilterWhere(['like', 'smis.org_courses.course_code', $course_code]);
            $query->andFilterWhere(['like', 'smis.cr_course_reg_type.course_reg_type_name', $course_reg_type_name]);
        }

        $query->groupBy([
            'smis.org_courses.course_id',
            'smis.org_courses.course_code',
            'smis.org_courses.course_name',
            'smis.cr_course_reg_type.course_reg_type_code',
            'smis.cr_course_reg_type.course_reg_type_name',
        ]);

        $dataProvider = new ActiveDataProvider([
            'query' => $query,
            'key' => 'course_id',
            'sort' => false,
        ]);


        $this->load($params);

        if (!$this->validate()) {
            // uncomment the following line if you do not want to return any records when validation fails
            // $query->where('0=1');
            return $dataProvider;
        }



        // $query
        //     ->andFilterWhere(['ilike', 'asess.acad_session_name', $this->acad_session_name])
        //     ->andFilterWhere(['ilike', 'prog.prog_code', $this->prog_code])
        //     ->andFilterWhere(['ilike', 'st.id_no', $this->id_no])
        //     ->andFilterWhere(['ilike', 'st.student_number', $this->student_number])
        //     ->andFilterWhere(['ilike', 'st.other_names', $this->other_names])
        //     ->andFilterWhere(['ilike', 'st.surname', $this->surname])
        //     ->andFilterWhere(['ilike', 'st.gender', $this->gender])
        //     ->andFilterWhere(['ilike', 'st.nationality', $this->nationality])
        //     ->andFilterWhere(['ilike', 'prog.prog_short_name', $this->prog_short_name])
        //     // ->andFilterWhere(['ilike', 'ss.sponsor_name', Yii::$app->request->get('sponsor_name')])

        // ;

        return $dataProvider;
    }


    /**
     * Creates data provider instance with search query applied
     *
     * @param array $params
     *
     * @return ActiveDataProvider
     */
    public function card($params)
    {
        $searchParams = Yii::$app->request->get('CoursesRegisteredSearch', []);
        $query = (new Query())
            ->select([
                'smis.org_courses.course_id',
                'smis.org_courses.course_code',
                'smis.org_courses.course_name',
                'smis.cr_course_reg_type.course_reg_type_code',
                'smis.cr_course_reg_type.course_reg_type_name',
                'smis.org_days.day_name',
                'smis.cr_prog_curr_timetable.exam_date',
                'smis.org_rooms.room_name',
                'smis.cr_programme_curr_lecture_timetable.start_time',
                'smis.cr_programme_curr_lecture_timetable.end_time',
                'date_format' => new Expression('TO_CHAR(smis.cr_prog_curr_timetable.exam_date::date, \'YYYY-MM-DD\')'),
                'start_time_format' => new Expression('TO_CHAR(smis.cr_programme_curr_lecture_timetable.start_time, \'HH12:MI AM\')'),
                'end_time_format' => new Expression('TO_CHAR(smis.cr_programme_curr_lecture_timetable.end_time, \'HH12:MI AM\')'),
            ])
            ->from('smis.cr_course_registration')
            ->innerJoin('smis.cr_prog_curr_timetable', 'smis.cr_course_registration.timetable_id = smis.cr_prog_curr_timetable.timetable_id')
            ->leftJoin('smis.cr_programme_curr_lecture_timetable', 'smis.cr_prog_curr_timetable.timetable_id = smis.cr_programme_curr_lecture_timetable.timetable_id')
            ->leftJoin('smis.org_rooms', 'cr_programme_curr_lecture_timetable.lecture_room_id = org_rooms.room_id')
            ->leftJoin('smis.org_days', 'smis.org_days.day_id  = smis.cr_programme_curr_lecture_timetable.day_id')
            ->innerJoin('smis.org_prog_curr_semester_group', 'smis.cr_prog_curr_timetable.prog_curriculum_sem_group_id = smis.org_prog_curr_semester_group.prog_curriculum_sem_group_id')
            ->innerJoin('smis.org_prog_curr_semester', 'smis.org_prog_curr_semester_group.prog_curriculum_semester_id = smis.org_prog_curr_semester.prog_curriculum_semester_id')
            ->leftJoin('smis.org_prog_level', 'smis.org_prog_curr_semester_group.programme_level = smis.org_prog_level.programme_level_id')
            ->innerJoin('smis.org_programme_curriculum', 'smis.org_prog_curr_semester.prog_curriculum_id = smis.org_programme_curriculum.prog_curriculum_id')
            ->innerJoin('smis.org_prog_curr_unit', 'smis.org_programme_curriculum.prog_curriculum_id = smis.org_prog_curr_unit.prog_curriculum_id')
            ->innerJoin('smis.org_unit_history', 'smis.org_prog_curr_unit.org_unit_history_id = smis.org_unit_history.org_unit_history_id')
            ->innerJoin('smis.org_unit', 'smis.org_unit_history.org_unit_id = smis.org_unit.unit_id')
            ->innerJoin('smis.org_programmes', 'smis.org_programme_curriculum.prog_id = smis.org_programmes.prog_id')
            ->innerJoin('smis.org_academic_session_semester', 'smis.org_prog_curr_semester.acad_session_semester_id = smis.org_academic_session_semester.acad_session_semester_id')
            ->innerJoin('smis.org_semester_code', 'smis.org_semester_code.semester_code = smis.org_academic_session_semester.semester_code')
            ->innerJoin('smis.org_academic_session', 'smis.org_academic_session_semester.acad_session_id = smis.org_academic_session.acad_session_id')
            ->innerJoin('smis.org_prog_curr_course', 'smis.cr_prog_curr_timetable.prog_curriculum_course_id = smis.org_prog_curr_course.prog_curriculum_course_id')
            ->innerJoin('smis.org_courses', 'smis.org_prog_curr_course.course_id = smis.org_courses.course_id')
            ->innerJoin('smis.cr_course_reg_type', 'smis.cr_course_registration.course_registration_type_id = smis.cr_course_reg_type.course_reg_type_id')
            ->innerJoin('smis.org_semester_type', 'smis.org_prog_curr_semester.semester_type_id = smis.org_semester_type.semester_type_id')
            ->innerJoin('smis.org_study_centre_group', 'smis.org_prog_curr_semester_group.study_centre_group_id = smis.org_study_centre_group.study_centre_group_id')
            ->innerJoin('smis.org_study_centre', 'smis.org_study_centre_group.study_centre_id = smis.org_study_centre.study_centre_id')
            ->innerJoin('smis.org_study_group', 'smis.org_study_centre_group.study_group_id = smis.org_study_group.study_group_id')
            ->innerJoin('smis.sm_student', 'smis.cr_course_registration.registration_number = smis.sm_student.student_number')
            ->where([
                'smis.org_programmes.prog_id' => Yii::$app->request->get('prog_id'),
                'smis.org_academic_session.acad_session_id' => Yii::$app->request->get('acad_session_id'),
                'smis.org_prog_level.programme_level_name' => Yii::$app->request->get('programme_level_name'),
                'smis.org_semester_code.semster_name' => Yii::$app->request->get('semster_name'),
                'smis.org_study_group.study_group_name' => Yii::$app->request->get('study_group_name'),
                'smis.org_semester_type.semester_type' => Yii::$app->request->get('semester_type'),
                'smis.sm_student.student_id' => Yii::$app->request->get('student_id'),
                'smis.org_unit.unit_id' => Yii::$app->request->get('unit_id')
            ]);
        if (!empty($searchParams)) {
            $course_code = $params['CoursesRegisteredSearch']['course_code'] ?? '';
            $course_reg_type_name = $params['CoursesRegisteredSearch']['course_reg_type_name'] ?? '';

            $query->andFilterWhere(['like', 'smis.org_courses.course_code', $course_code]);
            $query->andFilterWhere(['like', 'smis.cr_course_reg_type.course_reg_type_name', $course_reg_type_name]);
        }
        $query->groupBy([
            'smis.org_courses.course_id',
            'smis.org_courses.course_code',
            'smis.org_courses.course_name',
            'smis.cr_course_reg_type.course_reg_type_code',
            'smis.cr_course_reg_type.course_reg_type_name',
            'smis.org_days.day_name',
            'smis.cr_prog_curr_timetable.exam_date',
            'smis.org_rooms.room_name',
            'smis.cr_programme_curr_lecture_timetable.start_time',
            'smis.cr_programme_curr_lecture_timetable.end_time'
        ]);



        $dataProvider = new ActiveDataProvider([
            'query' => $query,
            'key' => 'course_id',
            'sort' => false,
        ]);


        $this->load($params);

        if (!$this->validate()) {
            // uncomment the following line if you do not want to return any records when validation fails
            // $query->where('0=1');
            return $dataProvider;
        }

        return $dataProvider;
    }


    /**
     * Creates data provider instance with search query applied
     *
     * @param array $params
     *
     * @return ActiveDataProvider
     */
    public function exam($params)
    {
        $query = (new Query())
            ->select([
                'smis.sm_student.student_id',
                'smis.sm_student.student_number',
                'smis.sm_student.surname',
                'smis.sm_student.other_names',
                'smis.cr_course_reg_type.course_reg_type_code',
                'smis.cr_course_reg_type.course_reg_type_name'
            ])
            ->from('smis.cr_course_registration')
            ->innerJoin('smis.cr_prog_curr_timetable', 'smis.cr_course_registration.timetable_id = smis.cr_prog_curr_timetable.timetable_id')
            ->innerJoin('smis.org_prog_curr_semester_group', 'smis.cr_prog_curr_timetable.prog_curriculum_sem_group_id = smis.org_prog_curr_semester_group.prog_curriculum_sem_group_id')
            ->innerJoin('smis.org_prog_curr_semester', 'smis.org_prog_curr_semester_group.prog_curriculum_semester_id = smis.org_prog_curr_semester.prog_curriculum_semester_id')
            ->leftJoin('smis.org_prog_level', 'smis.org_prog_curr_semester_group.programme_level = smis.org_prog_level.programme_level_id')
            ->innerJoin('smis.org_programme_curriculum', 'smis.org_prog_curr_semester.prog_curriculum_id = smis.org_programme_curriculum.prog_curriculum_id')
            ->innerJoin('smis.org_programmes', 'smis.org_programme_curriculum.prog_id = smis.org_programmes.prog_id')
            ->innerJoin('smis.org_academic_session_semester', 'smis.org_prog_curr_semester.acad_session_semester_id = smis.org_academic_session_semester.acad_session_semester_id')
            ->innerJoin('smis.org_semester_code', 'smis.org_semester_code.semester_code = smis.org_academic_session_semester.semester_code')
            ->innerJoin('smis.org_academic_session', 'smis.org_academic_session_semester.acad_session_id = smis.org_academic_session.acad_session_id')
            ->innerJoin('smis.org_prog_curr_course', 'smis.cr_prog_curr_timetable.prog_curriculum_course_id = smis.org_prog_curr_course.prog_curriculum_course_id')
            ->innerJoin('smis.org_courses', 'smis.org_prog_curr_course.course_id = smis.org_courses.course_id')
            ->innerJoin('smis.cr_course_reg_type', 'smis.cr_course_registration.course_registration_type_id = smis.cr_course_reg_type.course_reg_type_id')
            ->innerJoin('smis.org_semester_type', 'smis.org_prog_curr_semester.semester_type_id = smis.org_semester_type.semester_type_id')
            ->innerJoin('smis.org_study_centre_group', 'smis.org_prog_curr_semester_group.study_centre_group_id = smis.org_study_centre_group.study_centre_group_id')
            ->innerJoin('smis.org_study_centre', 'smis.org_study_centre_group.study_centre_id = smis.org_study_centre.study_centre_id')
            ->innerJoin('smis.org_study_group', 'smis.org_study_centre_group.study_group_id = smis.org_study_group.study_group_id')
            ->innerJoin('smis.sm_student', 'smis.cr_course_registration.registration_number = smis.sm_student.student_number')
            ->where([
                'smis.org_programmes.prog_id' => Yii::$app->request->get('prog_id'),
                'smis.org_academic_session.acad_session_id' => Yii::$app->request->get('acad_session_id'),
                'smis.org_prog_level.programme_level_name' => Yii::$app->request->get('programme_level_name'),
                'smis.org_semester_code.semster_name' => Yii::$app->request->get('semster_name'),
                'smis.org_study_group.study_group_name' => Yii::$app->request->get('study_group_name'),
                'smis.org_courses.course_id' => Yii::$app->request->get('course_id'),
                'smis.org_semester_type.semester_type' => Yii::$app->request->get('semester_type'),
            ])
            ->groupBy([
                'smis.sm_student.student_id',
                'smis.sm_student.student_number',
                'smis.sm_student.surname',
                'smis.sm_student.other_names',
                'smis.cr_course_reg_type.course_reg_type_code',
                'smis.cr_course_reg_type.course_reg_type_name'
            ]);


        $dataProvider = new ActiveDataProvider([
            'query' => $query,
            'key' => 'course_reg_type_code',
            'sort' => false,
        ]);


        $this->load($params);

        if (!$this->validate()) {
            // uncomment the following line if you do not want to return any records when validation fails
            // $query->where('0=1');
            return $dataProvider;
        }



        // $query
        //     ->andFilterWhere(['ilike', 'asess.acad_session_name', $this->acad_session_name])
        //     ->andFilterWhere(['ilike', 'prog.prog_code', $this->prog_code])
        //     ->andFilterWhere(['ilike', 'st.id_no', $this->id_no])
        //     ->andFilterWhere(['ilike', 'st.student_number', $this->student_number])
        //     ->andFilterWhere(['ilike', 'st.other_names', $this->other_names])
        //     ->andFilterWhere(['ilike', 'st.surname', $this->surname])
        //     ->andFilterWhere(['ilike', 'st.gender', $this->gender])
        //     ->andFilterWhere(['ilike', 'st.nationality', $this->nationality])
        //     ->andFilterWhere(['ilike', 'prog.prog_short_name', $this->prog_short_name])
        //     // ->andFilterWhere(['ilike', 'ss.sponsor_name', Yii::$app->request->get('sponsor_name')])

        // ;

        return $dataProvider;
    }



    /**
     * Creates data provider instance with search query applied
     *
     * @param array $params
     *
     * @return ActiveDataProvider
     */
    public function programmes($params)
    {
        $searchParams = Yii::$app->request->get('CoursesRegisteredSearch', []);
        $query = (new Query())
            ->select([
                'smis.org_programmes.prog_id',
                'smis.org_programmes.prog_code',
                'smis.org_programmes.prog_short_name',
                'smis.org_programmes.prog_full_name',
                'smis.org_unit.unit_id',
                'smis.org_unit.unit_name',
                'student_count' => new Expression('COUNT(DISTINCT smis.sm_student.student_number)'),
                'course_count' => new Expression('COUNT(DISTINCT smis.org_courses.course_id)'),
            ])
            ->from('smis.cr_course_registration')
            ->innerJoin('smis.cr_prog_curr_timetable', 'smis.cr_course_registration.timetable_id = smis.cr_prog_curr_timetable.timetable_id')
            ->innerJoin('smis.org_prog_curr_semester_group', 'smis.cr_prog_curr_timetable.prog_curriculum_sem_group_id = smis.org_prog_curr_semester_group.prog_curriculum_sem_group_id')
            ->innerJoin('smis.org_prog_curr_semester', 'smis.org_prog_curr_semester_group.prog_curriculum_semester_id = smis.org_prog_curr_semester.prog_curriculum_semester_id')
            ->innerJoin('smis.org_programme_curriculum', 'smis.org_prog_curr_semester.prog_curriculum_id = smis.org_programme_curriculum.prog_curriculum_id')
            ->innerJoin('smis.org_prog_curr_unit', 'smis.org_programme_curriculum.prog_curriculum_id = smis.org_prog_curr_unit.prog_curriculum_id')
            ->innerJoin('smis.org_unit_history', 'smis.org_prog_curr_unit.org_unit_history_id = smis.org_unit_history.org_unit_history_id')
            ->innerJoin('smis.org_unit', 'smis.org_unit_history.org_unit_id = smis.org_unit.unit_id')
            ->innerJoin('smis.org_programmes', 'smis.org_programme_curriculum.prog_id = smis.org_programmes.prog_id')
            ->innerJoin('smis.org_academic_session_semester', 'smis.org_prog_curr_semester.acad_session_semester_id = smis.org_academic_session_semester.acad_session_semester_id')
            ->innerJoin('smis.org_academic_session', 'smis.org_academic_session_semester.acad_session_id = smis.org_academic_session.acad_session_id')
            ->innerJoin('smis.org_prog_curr_course', 'smis.cr_prog_curr_timetable.prog_curriculum_course_id = smis.org_prog_curr_course.prog_curriculum_course_id')
            ->innerJoin('smis.org_courses', 'smis.org_prog_curr_course.course_id = smis.org_courses.course_id')
            ->innerJoin('smis.cr_course_reg_type', 'smis.cr_course_registration.course_registration_type_id = smis.cr_course_reg_type.course_reg_type_id')
            ->innerJoin('smis.org_semester_type', 'smis.org_prog_curr_semester.semester_type_id = smis.org_semester_type.semester_type_id')
            ->innerJoin('smis.org_study_centre_group', 'smis.org_prog_curr_semester_group.study_centre_group_id = smis.org_study_centre_group.study_centre_group_id')
            ->innerJoin('smis.org_study_centre', 'smis.org_study_centre_group.study_centre_id = smis.org_study_centre.study_centre_id')
            ->innerJoin('smis.org_study_group', 'smis.org_study_centre_group.study_group_id = smis.org_study_group.study_group_id')
            ->innerJoin('smis.sm_student', 'smis.cr_course_registration.registration_number = smis.sm_student.student_number');
        if (!empty($searchParams)) {
            $prog_code = $params['CoursesRegisteredSearch']['prog_code'] ?? '';
            $acad_session_id = $params['CoursesRegisteredSearch']['acad_session_id'] ?? 0;
            $unit_name = $params['CoursesRegisteredSearch']['unit_name'] ?? '';

            // dd($unit_name);
            if (!empty($acad_session_id)) {
                $query->where([
                    'smis.org_academic_session.acad_session_id' => $acad_session_id,
                ]);
            }
            $query->andFilterWhere(['like', 'smis.org_programmes.prog_code', $prog_code]);
            $query->andFilterWhere(['like', 'smis.org_unit.unit_name', $unit_name]);
        }
        $query->groupBy([
            'smis.org_unit.unit_id',
            'smis.org_unit.unit_name',
            'smis.org_programmes.prog_id',
            'smis.org_programmes.prog_code',
            'smis.org_programmes.prog_short_name',
            'smis.org_programmes.prog_full_name',
        ]);

        $query->andFilterWhere([
            '' => $this->prog_short_name
        ]);






        $dataProvider = new ActiveDataProvider([
            'query' => $query,
            'key' => 'prog_id',
            'sort' => false,
        ]);


        $this->load($params);

        if (!$this->validate()) {
            // uncomment the following line if you do not want to return any records when validation fails
            // $query->where('0=1');
            return $dataProvider;
        }

        return $dataProvider;
    }



    /**
     * Creates data provider instance with search query applied
     *
     * @param array $params
     *
     * @return ActiveDataProvider
     */
    public function year($params)
    {
        $searchParams = Yii::$app->request->get('CoursesRegisteredSearch', []);
        $query = (new Query())
            ->select([
                'smis.org_prog_level.programme_level_id',
                'smis.org_prog_level.programme_level_name',
                'smis.org_semester_code.semster_name',
                'smis.org_study_group.study_group_id',
                'smis.org_study_group.study_group_name',
                'smis.org_prog_curr_semester.semester_type_id',
                'smis.org_semester_type.semester_type',
                'student_count' => new Expression('COUNT(DISTINCT smis.sm_student.student_number)'),
                'course_count' => new Expression('COUNT(DISTINCT smis.org_courses.course_id)'),
            ])
            ->from('smis.cr_course_registration')
            ->innerJoin('smis.cr_prog_curr_timetable', 'smis.cr_course_registration.timetable_id = smis.cr_prog_curr_timetable.timetable_id')
            ->innerJoin('smis.org_prog_curr_semester_group', 'smis.cr_prog_curr_timetable.prog_curriculum_sem_group_id = smis.org_prog_curr_semester_group.prog_curriculum_sem_group_id')
            ->innerJoin('smis.org_prog_curr_semester', 'smis.org_prog_curr_semester_group.prog_curriculum_semester_id = smis.org_prog_curr_semester.prog_curriculum_semester_id')
            ->leftJoin('smis.org_prog_level', 'smis.org_prog_curr_semester_group.programme_level = smis.org_prog_level.programme_level_id')
            ->innerJoin('smis.org_programme_curriculum', 'smis.org_prog_curr_semester.prog_curriculum_id = smis.org_programme_curriculum.prog_curriculum_id')
            ->innerJoin('smis.org_prog_curr_unit', 'smis.org_programme_curriculum.prog_curriculum_id = smis.org_prog_curr_unit.prog_curriculum_id')
            ->innerJoin('smis.org_unit_history', 'smis.org_prog_curr_unit.org_unit_history_id = smis.org_unit_history.org_unit_history_id')
            ->innerJoin('smis.org_unit', 'smis.org_unit_history.org_unit_id = smis.org_unit.unit_id')
            ->innerJoin('smis.org_programmes', 'smis.org_programme_curriculum.prog_id = smis.org_programmes.prog_id')
            ->innerJoin('smis.org_academic_session_semester', 'smis.org_prog_curr_semester.acad_session_semester_id = smis.org_academic_session_semester.acad_session_semester_id')
            ->innerJoin('smis.org_semester_code', 'smis.org_semester_code.semester_code = smis.org_academic_session_semester.semester_code')
            ->innerJoin('smis.org_academic_session', 'smis.org_academic_session_semester.acad_session_id = smis.org_academic_session.acad_session_id')
            ->innerJoin('smis.org_prog_curr_course', 'smis.cr_prog_curr_timetable.prog_curriculum_course_id = smis.org_prog_curr_course.prog_curriculum_course_id')
            ->innerJoin('smis.org_courses', 'smis.org_prog_curr_course.course_id = smis.org_courses.course_id')
            ->innerJoin('smis.cr_course_reg_type', 'smis.cr_course_registration.course_registration_type_id = smis.cr_course_reg_type.course_reg_type_id')
            ->innerJoin('smis.org_semester_type', 'smis.org_prog_curr_semester.semester_type_id = smis.org_semester_type.semester_type_id')
            ->innerJoin('smis.org_study_centre_group', 'smis.org_prog_curr_semester_group.study_centre_group_id = smis.org_study_centre_group.study_centre_group_id')
            ->innerJoin('smis.org_study_centre', 'smis.org_study_centre_group.study_centre_id = smis.org_study_centre.study_centre_id')
            ->innerJoin('smis.org_study_group', 'smis.org_study_centre_group.study_group_id = smis.org_study_group.study_group_id')
            ->innerJoin('smis.sm_student', 'smis.cr_course_registration.registration_number = smis.sm_student.student_number')
            ->where([
                'smis.org_unit.unit_id' => Yii::$app->request->get('unit_id'),
                'smis.org_programmes.prog_id' => Yii::$app->request->get('prog_id'),
                'smis.org_academic_session_semester.acad_session_id' => Yii::$app->request->get('acad_session_id')
            ]);
        if (!empty($searchParams)) {
            $study_group_name = $params['CoursesRegisteredSearch']['study_group_name'] ?? '';
            $semster_name = $params['CoursesRegisteredSearch']['semster_name'] ?? '';
            $semester_type = $params['CoursesRegisteredSearch']['semester_type'] ?? '';
            $programme_level_name = $params['CoursesRegisteredSearch']['programme_level_name'] ?? '';

            // unit_name


            $query->andFilterWhere(['like', 'smis.org_study_group.study_group_name', $study_group_name]);
            $query->andFilterWhere(['like', 'smis.org_semester_code.semster_name', $semster_name]);
            $query->andFilterWhere(['like', 'smis.org_semester_type.semester_type', $semester_type]);
            $query->andFilterWhere(['like', 'smis.org_prog_level.programme_level_name', $programme_level_name]);
        }
        $query->groupBy([
            'smis.org_prog_level.programme_level_id',
            'smis.org_academic_session_semester.acad_session_semester_desc',
            'smis.org_semester_code.semster_name',
            'smis.org_study_group.study_group_id',
            'smis.org_prog_curr_semester.semester_type_id',
            'smis.org_semester_type.semester_type',
        ]);


        // dd($query->all());




        $dataProvider = new ActiveDataProvider([
            'query' => $query,
            'key' => 'programme_level_id',
            'sort' => false,
        ]);


        $this->load($params);

        if (!$this->validate()) {
            // uncomment the following line if you do not want to return any records when validation fails
            // $query->where('0=1');
            return $dataProvider;
        }

        return $dataProvider;
    }


    /**
     * Creates data provider instance with search query applied
     *
     * @param array $params
     *
     * @return ActiveDataProvider
     */
    public function students($params)
    {
        $searchParams = Yii::$app->request->get('CoursesRegisteredSearch', []);
        $query = (new Query())
            ->select([
                'smis.sm_student.student_id',
                'smis.sm_student.gender',
                'smis.sm_student.student_id',
                'smis.sm_student.student_number',
                'smis.sm_student.surname',
                'smis.sm_student.other_names',
                'smis.sm_student.gender',
                'smis.sm_student.primary_email',
                'smis.sm_student.primary_phone_no',
                'smis.sm_student.registration_date'
            ])
            ->from('smis.cr_course_registration')
            ->innerJoin('smis.cr_prog_curr_timetable', 'smis.cr_course_registration.timetable_id = smis.cr_prog_curr_timetable.timetable_id')
            ->innerJoin('smis.org_prog_curr_semester_group', 'smis.cr_prog_curr_timetable.prog_curriculum_sem_group_id = smis.org_prog_curr_semester_group.prog_curriculum_sem_group_id')
            ->innerJoin('smis.org_prog_curr_semester', 'smis.org_prog_curr_semester_group.prog_curriculum_semester_id = smis.org_prog_curr_semester.prog_curriculum_semester_id')
            ->leftJoin('smis.org_prog_level', 'smis.org_prog_curr_semester_group.programme_level = smis.org_prog_level.programme_level_id')
            ->innerJoin('smis.org_programme_curriculum', 'smis.org_prog_curr_semester.prog_curriculum_id = smis.org_programme_curriculum.prog_curriculum_id')
            ->innerJoin('smis.org_prog_curr_unit', 'smis.org_programme_curriculum.prog_curriculum_id = smis.org_prog_curr_unit.prog_curriculum_id')
            ->innerJoin('smis.org_unit_history', 'smis.org_prog_curr_unit.org_unit_history_id = smis.org_unit_history.org_unit_history_id')
            ->innerJoin('smis.org_unit', 'smis.org_unit_history.org_unit_id = smis.org_unit.unit_id')
            ->innerJoin('smis.org_programmes', 'smis.org_programme_curriculum.prog_id = smis.org_programmes.prog_id')
            ->innerJoin('smis.org_academic_session_semester', 'smis.org_prog_curr_semester.acad_session_semester_id = smis.org_academic_session_semester.acad_session_semester_id')
            ->innerJoin('smis.org_semester_code', 'smis.org_semester_code.semester_code = smis.org_academic_session_semester.semester_code')
            ->innerJoin('smis.org_academic_session', 'smis.org_academic_session_semester.acad_session_id = smis.org_academic_session.acad_session_id')
            ->innerJoin('smis.org_prog_curr_course', 'smis.cr_prog_curr_timetable.prog_curriculum_course_id = smis.org_prog_curr_course.prog_curriculum_course_id')
            ->innerJoin('smis.org_courses', 'smis.org_prog_curr_course.course_id = smis.org_courses.course_id')
            ->innerJoin('smis.cr_course_reg_type', 'smis.cr_course_registration.course_registration_type_id = smis.cr_course_reg_type.course_reg_type_id')
            ->innerJoin('smis.org_semester_type', 'smis.org_prog_curr_semester.semester_type_id = smis.org_semester_type.semester_type_id')
            ->innerJoin('smis.org_study_centre_group', 'smis.org_prog_curr_semester_group.study_centre_group_id = smis.org_study_centre_group.study_centre_group_id')
            ->innerJoin('smis.org_study_centre', 'smis.org_study_centre_group.study_centre_id = smis.org_study_centre.study_centre_id')
            ->innerJoin('smis.org_study_group', 'smis.org_study_centre_group.study_group_id = smis.org_study_group.study_group_id')
            ->innerJoin('smis.sm_student', 'smis.cr_course_registration.registration_number = smis.sm_student.student_number')
            ->where([
                'smis.org_programmes.prog_id' => Yii::$app->request->get('prog_id'),
                'smis.org_academic_session_semester.acad_session_id' => Yii::$app->request->get('acad_session_id'),
                'smis.org_prog_level.programme_level_name' => Yii::$app->request->get('programme_level_name'),
                'smis.org_semester_code.semster_name' => Yii::$app->request->get('semster_name'),
                'smis.org_semester_type.semester_type' => Yii::$app->request->get('semester_type'),
                'smis.org_study_group.study_group_name' => Yii::$app->request->get('study_group_name'),
                'smis.org_unit.unit_id' => Yii::$app->request->get('unit_id')
            ]);
        if (!empty($searchParams)) {
            $student_number = $params['CoursesRegisteredSearch']['student_number'] ?? '';
            $surname = $params['CoursesRegisteredSearch']['surname'] ?? '';
            $other_names = $params['CoursesRegisteredSearch']['other_names'] ?? '';

            $query->andFilterWhere(['like', 'smis.sm_student.student_number', $student_number]);
            $query->andFilterWhere(['like', 'smis.sm_student.surname', $surname]);
            $query->andFilterWhere(['like', 'smis.sm_student.other_names', $other_names]);
        }
        $query->groupBy([
            'smis.sm_student.student_id',
            'smis.sm_student.gender',
            'smis.sm_student.student_id',
            'smis.sm_student.student_number',
            'smis.sm_student.surname',
            'smis.sm_student.other_names',
            'smis.sm_student.gender',
            'smis.sm_student.primary_email',
            'smis.sm_student.primary_phone_no',
            'smis.sm_student.registration_date'
        ]);

        $dataProvider = new ActiveDataProvider([
            'query' => $query,
            'key' => 'student_id',
            'sort' => false,
        ]);


        $this->load($params);

        if (!$this->validate()) {
            // uncomment the following line if you do not want to return any records when validation fails
            // $query->where('0=1');
            return $dataProvider;
        }

        $query
            ->andFilterWhere(['ilike', 'smis.org_courses.course_name', $this->course_name])
            // ->andFilterWhere(['ilike', 'ss.sponsor_name', Yii::$app->request->get('sponsor_name')])

        ;

        return $dataProvider;
    }
}

```