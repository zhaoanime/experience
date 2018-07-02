```html
<form class="js-ajax-form" action="{:U('user/login/dologin')}" method="post">
    <label for="input_username">账号</label>
    <input type="text" id="input_username" name="username" placeholder="请输入用户名或者邮箱" class="span3">

    <label for="input_password">密码</label>
    <input type="password" id="input_password" name="password" placeholder="请输入密码" class="span3">

    <label for="input_verify">验证码</label>
    <input type="text" id="input_verify" name="verify"  placeholder="请输入验证码" class="span3">
    {:sp_verifycode_img('length=4&font_size=15&width=100&height=35&charset=1234567890')}
    <button class="btn btn-primary js-ajax-submit" type="submit" data-wait="1500">确定</button>
</form>
```
**加上类名为 js-ajax-form 的 form标签，配合类名为 js-ajax-submit 的提交按钮**
在用户单击提交按钮时，会以 ajax 的方式提交表单，提交的地址为 form 的 action属性，提交方法为 form的 method 属性，凡是在 此form 里且有 name 属性的表单元素都会被提交

