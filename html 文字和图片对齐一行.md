```html
<h1 class="fl web-logo" style="position: relative;width: 330px;">
        <a href="{:U('Index/index')}" style="width: 100%;height: 100%;display: block;">
            <img src="{:cmf_get_image_url($config.thumbpic)}" style="height: 66px;transform: translateY(-50%);position: absolute;top: 50%;left: 0;">
            <span style="line-height: 66px;color: #fff;transform: translateY(-50%);position: absolute;top: 50%;right: 0;">{$config.title}</span>
        </a>
    </h1>
```