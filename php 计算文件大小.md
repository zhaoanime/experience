
```PHP
function count_size($bit){
        $type = array('Bytes','KB','MB','GB','TB');
        for($i = 0; $bit >= 1024; $i++){
            $bit/=1024;//单位每增大1024，则单位数组向后移动一位表示相应的单位
        }
        return (floor($bit*100)/100).$type[$i];
        //floor是取整函数，为了防止出现一串的小数，这里取了两位小数
}
```
调用时
```php
$filename = dirname(__FILE__).DS."..".DS."..".DS."..".DS."upload".DS.$post['file_urls'];
$data['post']['size']=$this->count_size(filesize($filename));
```

