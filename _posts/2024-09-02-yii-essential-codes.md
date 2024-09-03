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