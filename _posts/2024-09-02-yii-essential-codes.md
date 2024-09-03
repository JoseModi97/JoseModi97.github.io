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
                            'type' => GridView::BS_HIDDEN_SM
                        ],
                        'showFooter' => true,
                        'export' => [
                            'fontAwesome' => true
                        ],
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