---
title: Yii Search Query
description: A blog post on how I used query builder to perform advanced searched
author: modi
date: 2024-08-09 13:43:00 +0800
categories: [Yiiframework, SearchQuery]
tags: [php]
pin: false
math: true
mermaid: true
---

## Understanding the Yii2 Search Model: A Deep Dive into search($params)

In Yii2, the search model is a crucial component when dealing with data filtering and retrieval in grid views. One of its core functions is search($params), which empowers developers to create complex queries with ease. This post will explore a practical example, illustrating how to leverage the search model to execute intricate database queries.

## The search($params) Function
The search($params) function is designed to process incoming search parameters and apply them to a query. This function typically resides in a model class that extends \yii\base\Model or \yii\db\ActiveRecord.

Here's a breakdown of how you can implement the function using the provided query example:

## Constructing the Subquery
First, we need to create a subquery that gathers necessary data before performing aggregations:

```php
$subQuery = (new \yii\db\Query())
    ->select([
        'ss.student_id',
        'ss.gender',
        'op.prog_full_name',
    ])
    ->from('smis.sm_student ss')
    ->innerJoin('smis.sm_student_programme_curriculum spc', 'spc.student_id = ss.student_id')
    ->innerJoin('smis.sm_academic_progress sap', 'sap.student_prog_curriculum_id = spc.student_prog_curriculum_id')
    ->innerJoin('smis.org_academic_levels oal', 'oal.academic_level_id = sap.academic_level_id')
    ->innerJoin('smis.org_academic_session oas', 'oas.acad_session_id = sap.acad_session_id')
    ->innerJoin('smis.org_programme_curriculum opc', 'spc.prog_curriculum_id = opc.prog_curriculum_id')
    ->innerJoin('smis.org_programmes op', 'op.prog_id = opc.prog_id')
    ->where(['oas.acad_session_id' => $params['acad_session_id']])
    ->distinct();
```

## Building the Main Query
The main query executes aggregations on the subquery results, providing insights into the number of male and female students per program:

```php
$query = (new \yii\db\Query())
    ->select([
        'prog_full_name',
        new \yii\db\Expression('SUM(CASE WHEN gender = \'M\' THEN 1 ELSE 0 END) AS MALE'),
        new \yii\db\Expression('SUM(CASE WHEN gender = \'F\' THEN 1 ELSE 0 END) AS FEMALE'),
    ])
    ->from(['sub' => $subQuery])
    ->groupBy(['prog_full_name']);
```

## Integrating into search($params)
Here's how you might integrate this into a search model's search function:

```php
public function search($params)
{
    $subQuery = (new \yii\db\Query())
        ->select([
            'ss.student_id',
            'ss.gender',
            'op.prog_full_name',
        ])
        ->from('smis.sm_student ss')
        ->innerJoin('smis.sm_student_programme_curriculum spc', 'spc.student_id = ss.student_id')
        ->innerJoin('smis.sm_academic_progress sap', 'sap.student_prog_curriculum_id = spc.student_prog_curriculum_id')
        ->innerJoin('smis.org_academic_levels oal', 'oal.academic_level_id = sap.academic_level_id')
        ->innerJoin('smis.org_academic_session oas', 'oas.acad_session_id = sap.acad_session_id')
        ->innerJoin('smis.org_programme_curriculum opc', 'spc.prog_curriculum_id = opc.prog_curriculum_id')
        ->innerJoin('smis.org_programmes op', 'op.prog_id = opc.prog_id')
        ->where(['oas.acad_session_id' => $params['acad_session_id']])
        ->distinct();

    $query = (new \yii\db\Query())
        ->select([
            'prog_full_name',
            new \yii\db\Expression('SUM(CASE WHEN gender = \'M\' THEN 1 ELSE 0 END) AS MALE'),
            new \yii\db\Expression('SUM(CASE WHEN gender = \'F\' THEN 1 ELSE 0 END) AS FEMALE'),
        ])
        ->from(['sub' => $subQuery])
        ->groupBy(['prog_full_name']);

    return $query->all();
}
```


## Conclusion
By effectively utilizing the search($params) function and Yii2's powerful query builder, you can manipulate and retrieve data with remarkable flexibility. This approach not only enhances code readability but also keeps your application logic clean and maintainable.


