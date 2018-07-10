```html
<input type="text" class="form-control" value="{$vo.list_order}" data-id="{$vo.id}" data-iform-id="{$id}" data-old="{$vo.list_order}" onchange="o_change(this)">
```
this到了js中就是此dom元素
data-* 属性用于存储私有页面后应用的自定义数据。
data-* 属性可以在所有的 HTML 元素中嵌入数据。
>
jq中的用法：
$(selector).data(name)
$(selector).data(name,value)
```javascript
function o_change(e){
    var    iform_id=$(e).attr("data-iform-id");
    var     item_id=$(e).attr("data-id");
    var     old_order=$(e).attr("data-old");
    var     new_order=$(e).vale();
   if(new_order!=old_order){
       $.post("{:url('editItemOrder)}",{
           "iform_id":iform_id,
           "item_id":item_id,
           "list_order":new_order
           },function(){
               
               },"json");
   }
}
```