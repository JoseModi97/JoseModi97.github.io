---
title: Enhancing Security with Yii2's Two-Factor Authentication (2FA)
description: A blog post on how to implement 2 factor authentication using yii
author: cotes
layout: post
date: 2024-08-04 08:56:00 +0800
categories: [Yiiframework, 2FA]
tags: [php]
pin: true
math: true
mermaid: true
image:
  path: https://raw.githubusercontent.com/JoseModi97/images/main/2fa.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: Responsive rendering of Chirpy theme on multiple devices.
---

## YII 2FA

![Desktop View](https://raw.githubusercontent.com/JoseModi97/images/main/_2b3f721b-4b61-4fab-af0d-34ab7492ba3b.jfif){: width="250" height="250" .w-70 .left}
In today's digital age, security is paramount. As developers, we need to ensure that our applications are safeguarded against unauthorized access. One effective way to bolster security is through Two-Factor Authentication (2FA). Yii2, a high-performance PHP framework, offers robust support for integrating 2FA. In this blog post, we'll explore how to implement 2FA in Yii2 and why it's a crucial feature for your application. 

In this blog post, we'll explore how to implement 2FA in Yii2 and why it's a crucial feature for your application. We'll begin by understanding the basics of 2FA and how it adds an extra layer of security beyond the traditional username and password. Then, we'll delve into the step-by-step process of setting up 2FA in a Yii2 application, covering both time-based one-time passwords (TOTP) and SMS-based verification methods.


## What is Two-Factor Authentication (2FA)?

Two-Factor Authentication adds an extra layer of security to the authentication process by requiring two forms of verification before granting access. Typically, this involves something the user knows (password) and something the user has (a mobile device or a security token). Even if an attacker manages to steal the password, they would still need the second factor to gain access.

## Benefits of 2FA
1. Enhanced Security: By requiring two forms of authentication, 2FA significantly reduces the risk of unauthorized access.
2. User Trust: Implementing 2FA shows users that you take their security seriously, which can increase trust and loyalty.
3. Compliance: Many regulations and standards (like GDPR and HIPAA) recommend or require 2FA for certain types of data access.


## Implementing 2FA in Yii2
### Step 1: Install the Required Packages
To get started with 2FA in Yii2, you'll need the yii2-2fa extension. You can install it via Composer:

```bash
composer require yii2-2fa/yii2-2fa
```
### Step 2: Configure the Component
Next, you need to configure the 2FA component in your Yii2 application. Open your configuration file (config/web.php or config/main.php) and add the following:
```php
'components' => [
    'twoFactorAuth' => [
        'class' => 'yii2-2fa\TwoFactorAuth',
        'issuer' => 'YourAppName', // The issuer name for the 2FA
    ],
    // Other components...
],
```

### Step 3: Modify the User Model
Your user model needs to support 2FA. Ensure your user table has columns for storing the 2FA secret key and the status. Then, modify your user model to include these fields:

```php
class User extends \yii\db\ActiveRecord implements \yii\web\IdentityInterface
{
    // Other attributes and methods...

    public $auth_key;
    public $twofa_secret;
    public $twofa_enabled;

    public function rules()
    {
        return [
            // Other rules...
            [['twofa_secret', 'twofa_enabled'], 'safe'],
        ];
    }

    public function enableTwoFactorAuth()
    {
        $this->twofa_secret = \Yii::$app->twoFactorAuth->generateSecretKey();
        $this->twofa_enabled = true;
        return $this->save();
    }

    public function disableTwoFactorAuth()
    {
        $this->twofa_secret = null;
        $this->twofa_enabled = false;
        return $this->save();
    }
}
```

### Step 4: Create the 2FA Setup and Verification Views
Create views to set up and verify 2FA. Here's an example of a setup view where users can scan a QR code to configure their authenticator app:

```php
<?php
use yii\helpers\Html;
use yii\widgets\ActiveForm;

/* @var $this yii\web\View */
/* @var $model common\models\User */

$this->title = 'Two-Factor Authentication Setup';
$this->params['breadcrumbs'][] = $this->title;
?>

<div class="twofa-setup">
    <h1><?= Html::encode($this->title) ?></h1>
    <p>Scan the QR code below with your authenticator app:</p>
    <img src="<?= Yii::$app->twoFactorAuth->getQRCodeUrl('YourAppName', $model->email, $model->twofa_secret) ?>" alt="QR Code">
    <p>Or enter this code manually: <strong><?= $model->twofa_secret ?></strong></p>

    <div class="form-group">
        <?= Html::a('Done', ['profile/index'], ['class' => 'btn btn-success']) ?>
    </div>
</div>
```

### Step 5: Verify 2FA During Login
Modify your login action to include 2FA verification. Here's an example:

```php
public function actionLogin()
{
    $model = new LoginForm();
    
    if ($model->load(Yii::$app->request->post()) && $model->login()) {
        $user = Yii::$app->user->identity;
        if ($user->twofa_enabled) {
            return $this->redirect(['site/twofa-verify']);
        }
        return $this->goBack();
    }
    
    return $this->render('login', [
        'model' => $model,
    ]);
}

public function actionTwofaVerify()
{
    $model = new TwofaForm();
    
    if ($model->load(Yii::$app->request->post()) && $model->validate()) {
        return $this->goBack();
    }
    
    return $this->render('twofa-verify', [
        'model' => $model,
    ]);
}
```

### Step 6: Create the 2FA Verification Form
Create a form for users to enter their 2FA code:

```php
<?php
use yii\helpers\Html;
use yii\widgets\ActiveForm;

/* @var $this yii\web\View */
/* @var $model app\models\TwofaForm */

$this->title = 'Two-Factor Authentication';
$this->params['breadcrumbs'][] = $this->title;
?>

<div class="twofa-verify">
    <h1><?= Html::encode($this->title) ?></h1>
    <p>Please enter the verification code from your authenticator app:</p>
    
    <?php $form = ActiveForm::begin(); ?>
    
    <?= $form->field($model, 'twofa_code')->textInput(['maxlength' => true]) ?>
    
    <div class="form-group">
        <?= Html::submitButton('Verify', ['class' => 'btn btn-primary']) ?>
    </div>
    
    <?php ActiveForm::end(); ?>
</div>
```

### Step 7: Validate the 2FA Code
Finally, add validation logic in the TwofaForm model:

```php
class TwofaForm extends \yii\base\Model
{
    public $twofa_code;

    public function rules()
    {
        return [
            [['twofa_code'], 'required'],
            [['twofa_code'], 'validateTwofaCode'],
        ];
    }

    public function validateTwofaCode($attribute, $params)
    {
        $user = Yii::$app->user->identity;
        if (!Yii::$app->twoFactorAuth->verifyCode($user->twofa_secret, $this->$attribute)) {
            $this->addError($attribute, 'Invalid verification code.');
        }
    }
}
```

## Conclusion
Implementing Two-Factor Authentication in Yii2 adds a vital layer of security to your application. By following the steps outlined above, you can enhance user trust and protect sensitive data from unauthorized access. Security is an ongoing process, and incorporating 2FA is a significant step towards making your application more resilient against threats.