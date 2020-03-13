DataTables widget for Yii2
===========================
This extension provides the [DataTables](https://github.com/DataTables/DataTables) integration for the Yii2 framework.

[![Latest Stable Version](https://poser.pugx.org/reine/yii2-widget-datatables/v/stable)](https://packagist.org/packages/reine/yii2-widget-datatables) [![Total Downloads](https://poser.pugx.org/reine/yii2-widget-datatables/downloads)](https://packagist.org/packages/reine/yii2-widget-datatables) [![Latest Unstable Version](https://poser.pugx.org/reine/yii2-widget-datatables/v/unstable)](https://packagist.org/packages/reine/yii2-widget-datatables) [![License](https://poser.pugx.org/reine/yii2-widget-datatables/license)](https://packagist.org/packages/reine/yii2-widget-datatables)

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```bash
composer require --prefer-dist reine/yii2-widget-datatables "^0.1.1"
```

or add

```
"reine/yii2-widget-datatables": "^0.1.1"
```

to the require section of your `composer.json` file.

Usage
-----
Use DataTables as any other other Yii2 widget.

```php
use reine\datatables\DataTables;
```

```php
<?php
    $searchModel = new ModelSearch();
    $dataProvider = $searchModel->search(Yii::$app->request->queryParams);
?>
<?= DataTables::widget([
    'dataProvider' => $dataProvider,
    'filterModel' => $searchModel,
    'columns' => [
        ['class' => 'yii\grid\SerialColumn'],

        //columns

        ['class' => 'yii\grid\ActionColumn'],
    ],
]);?>
```
This extension uses the Bootstrap 4 integration plugin to provide a Yii2 style by default.

The TableTools plugin is also available. Specify the DOM and the tableTools settings in the clientOptions array as the following example.

```php
...
'clientOptions' => [
    "lengthMenu"=> [[20,-1], [20,Yii::t('app',"All")]],
    "info"=>false,
    "responsive"=>true, 
    "dom"=> 'lfTrtip',
    "tableTools"=>[
        //empty for load button assets
    ],
    'buttons'   => ['copy', 'excel', 'pdf'],
],
...
```

You can also use DataTables in the JavaScript layer of your application. To achieve this, you need to include DataTables as a dependency of your Asset file. In this case, you could use yii\grid\GridView or using the datatables options retrieve => true to avoid errors. In both case all options must be in the Javascript object.

```php
public $depends = [
...
'reine\datatables\DataTablesAsset',
...
];
```
