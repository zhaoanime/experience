```php
$where['a.categoryid|c.parentids'] = [['eq', $category],['like', "%,".$category."%"],'or'];
```