
php url地址栏传中文乱码解决方法
urlencode函数采用UTF-8对URL进行编码，所以如果服务器在进行解码中文时使用的是其他的编码方式就会出现乱码，默认的服务器配置的解码字符集都不是UTF-8，所以大部分情况下地址栏提交中文查询参数时会产生乱码
```php
$searchkey=iconv( 'UTF-8','GBK', $searchkey);
```