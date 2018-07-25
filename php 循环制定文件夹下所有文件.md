php 循环制定文件夹下所有文件
```php
$handler = opendir('./ss/');//从根目录开始算的文件夹
//ss、./ss、./ss/效果一样
		while( ($filename = readdir($handler)) !== false ) {
		    if($filename != "." && $filename != ".."){
		        // echo $filename."<br>";
		        $tables[]=str_replace('.txt', '', $filename);
		    }
		}
		closedir($handler);
```