# swoft mongo db pool

```
composer require yumufeng/swoft-mongodb-pool
```

## config 
在/config/properties目录里面创建文件 mongodb.php
添加以下内容
```php
return [
    'appName'          => 'swoft-mongodb-connection',
    'minActive'        => 5,
    'maxActive'        => 1000,
    'userName'         => '',
    'password'         => '',
    'host'             => '127.0.0.1',
    'port'             => 27017,
    'dbName'           => 'test',
    'authMechanism'    => 'SCRAM-SHA-256',
    //设置复制集,没有不设置
    //'replica'          => 'rs0'
    
];
```

## config/properties/app.php 添加
```
'mongo' => require __DIR__ . DS . 'mongodb.php,
'components' => [
        'custom' => [
            // Your package namespace.
            'SwoftMongo\\',

        ],
    ]
```



# 使用案例

\SwoftMongo\MongoDB\Mongo 下面的静态方法直接使用

#### 查询

```php

```

#### 分页查询
```php
$list = Mongo::fetchPagination('article', 10, 0, ['author' => $author]);
```

#### count统计

```php
$filter = ['isGroup' => "0", 'wechat' => '15584044700'];
$count = Mongo::count('fans', $filter);
```