strpos函数返回boolean值.FALSE和TRUE不用多说.用 “===”进行判断.strpos在执行速度上都比以上两个函数快,另外strpos有一个参数指定判断的位置,但是默认为空.意思是判断整个字符串.缺点是对中文的支持不好.
##例一
```php
if(strpos('www.jb51.net','jb51') !== false){ 
 echo '包含jb51'; 
}else{
 echo '不包含jb51'; 
}
```
##例二
```php
$str= 'abc';
$needle= 'a';
$pos = strpos($str, $needle); // 返回第一次找到改字符串的位置，这里返回为1，若查不到则返回Fals
```