
**有时exec会被php.ini排除，需要打开，然后重启php-fpm服务**
在命令行最后添加“2>&1”就可以将返回的执行结果输出到ouptput数组，ret是错误代码
```php
    $re=exec("sudo python SendOrGetKafka.py p juping tj001 str  2>&1",$output, $ret);
    var_dump($output);
	 echo "<br>";
    var_dump($ret);
    echo "<br>";
    var_dump($re);
```
这段程序是在某模块的控制器下
但是
**这里SendOrGetKafka.py是在网站程序的根目录**