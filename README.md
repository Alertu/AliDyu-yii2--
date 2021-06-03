## 阿里短信通道(YII2)



#### 一：安装saviorlv/yii2-dysms拓展



composer地址：https://packagist.org/package...

```
composer require "saviorlv/yii2-dysms"
```





####  二：saviorlv/yii2-dysms拓展配置

```php
'components' => 
    [ ..... 'aliyun' =>
     [ 
         'class' =>'saviorlv\aliyun\Sms',
         'accessKeyId' => 'XXXXXX',//阿里云accessKeyId 
         'accessKeySecret' => 'XXXXXX'//阿里云accessKeySecret
     ],
     .... ] 
```





#### 三：实现短信发送



##### 1:单条短信发送

```php
$response = \Yii::$app->aliyun->sendSms( "短信签名", // 短信签名 "SMS_5002925", // 短信模板编号 "18551773287", // 短信接收者 //模板变量 [ "code"=>"12345", "product"=>"dsd" ], //发送短信流水号，选填 "123" ); 
```



##### 2:多条短信发送

```php
//批量发送(签名、手机号、模板字段 数组长度必须相等) 
$response = \Yii::$app->aliyun->sendBatchSms( // 短信签名 [ '短信签名', '短信签名' ], "SMS_5002925", // 短信模板编号 // 短信接收者 [ '18551773287', '17600827397' ], //模板变量 [ [ "code"=>"12345", "product"=>"测试" ], [ "code"=>"12345", "product"=>"测试" ], ], //发送短信流水号，选填 "123" ); 
```
