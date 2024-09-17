---
title: Result Slip Report
description: An Example of the layout of result slip
author: modi
date: 2024-09-17 09:18:00 +0800
categories: [Yiiframework, Essentials]
tags: [php]
pin: true
math: true
mermaid: true
---

```php
<?php

use yii\helpers\Html;
use yii\widgets\ListView;

// Prepare data for grouping
$results = $dataProvider->getModels();
$groupedData = [];

foreach ($results as $row) {
    $studentNumber = $row['student_number'];

    if (!isset($groupedData[$studentNumber])) {
        $groupedData[$studentNumber] = [
            'surname' => $row['surname'],
            'other_names' => $row['other_names'],
            'courses' => []
        ];
    }

    $groupedData[$studentNumber]['courses'][] = [
        'course_code' => $row['course_code'],
        'course_name' => $row['course_name'],
        'course_reg_type_name' => $row['course_reg_type_name'],
        'final_mark' => $row['final_mark']
    ];
}
?>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Course Report</title>
    <link rel="stylesheet" href="path/to/bootstrap.css">
    <style>
        .report-container {
            margin: 20px;
        }

        .student-section {
            border: 1px solid #ddd;
            border-radius: 5px;
            margin-bottom: 20px;
            padding: 15px;
            background-color: #f9f9f9;
        }

        .student-header {
            font-size: 1.5em;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .student-info {
            margin-bottom: 15px;
        }

        .courses-table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }

        .courses-table th,
        .courses-table td {
            border: 1px solid #ddd;
            padding: 8px;
        }

        .courses-table th {
            background-color: #f4f4f4;
            text-align: left;
        }

        .course-row:nth-child(even) {
            background-color: #f9f9f9;
        }

        .report-footer {
            font-size: 0.9em;
            text-align: right;
            margin-top: 20px;
        }
    </style>
</head>

<body>
    <div class="report-container">
        <h1>Student Course Report</h1>

        <?php foreach ($groupedData as $studentNumber => $studentData): ?>
            <div class="student-section">
                <div class="student-header">
                    <?= Html::encode($studentData['surname']) . ', ' . Html::encode($studentData['other_names']) . ' (Student Number: ' . Html::encode($studentNumber) . ')' ?>
                </div>

                <div class="student-info">
                    <strong>Student Number:</strong> <?= Html::encode($studentNumber) ?><br>
                    <strong>Surname:</strong> <?= Html::encode($studentData['surname']) ?><br>
                    <strong>Other Names:</strong> <?= Html::encode($studentData['other_names']) ?>
                </div>

                <table class="courses-table">
                    <thead>
                        <tr>
                            <th>Course Code</th>
                            <th>Course Name</th>
                            <th>Registration Type</th>
                            <th>Final Mark</th>
                        </tr>
                    </thead>
                    <tbody>
                        <?php foreach ($studentData['courses'] as $course): ?>
                            <tr class="course-row">
                                <td><?= Html::encode($course['course_code']) ?></td>
                                <td><?= Html::encode($course['course_name']) ?></td>
                                <td><?= Html::encode($course['course_reg_type_name']) ?></td>
                                <td><?= Html::encode($course['final_mark']) ?></td>
                            </tr>
                        <?php endforeach; ?>
                    </tbody>
                </table>
            </div>
        <?php endforeach; ?>

        <div class="report-footer">
            Report generated on <?= date('Y-m-d H:i:s') ?>
        </div>
    </div>
</body>

</html>
```
