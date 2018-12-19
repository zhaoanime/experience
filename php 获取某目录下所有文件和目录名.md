

```php
//获取某目录下所有文件、目录名（不包括子目录下文件、目录名）
echo __DIR__;
$handler = opendir(__DIR__);
while (($filename = readdir($handler)) !== false) {//务必使用!==，防止目录下出现类似文件名“0”等情况
if ($filename != "." && $filename != "..") {
        $files[] = $filename ;
   }
}
closedir($handler);
//打印所有文件名
foreach ($files as $value) {
	echo $value."<br />";
}
die;
```