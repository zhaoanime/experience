endif
```php
    if($user_id==1):$hide2='';
     elseif($user_id!=1&&in_array($key, ['siteurl','mobileurl'])):$hide2='hide';
     else:$hide2='';endif;
```