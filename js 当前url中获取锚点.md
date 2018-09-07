获取连接中的锚点
```javascript
var hash=window.location.hash;
    if(hash=='#C'){
        $('#wrapper').removeClass('active');
        $('#C').addClass('active');
        $('#Atab').removeClass('active');
        $('#Ctab').addClass('active');
    }
```
附：php paginate类设置参数带锚点
```php
//历史文件
            $result = db('asset')
            ->where(['suffix'=>['in',['png','jpg','jpeg','gif','bmp4','ico']]])
            ->order('create_time', 'DESC')
            ->paginate(10);
            $result->appends($this->request->param());
            $result->fragment('C');
            $this->assign('page', $result->render());
            $this->assign('assets', $result->items());
            return $this->fetch(":webuploader");
```