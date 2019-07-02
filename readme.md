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



## useage

```php
\SwoftMongo\MongoDB\Mongo 下面的静态方法直接使用

分页查询

$list = Mongo::fetchPagination('article', 10, 0, ['author' => $author]);
```
