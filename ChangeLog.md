## 2019 年 3 月 22 日 01 点 09 分

New feature support varable key some\_$admin$\_str.
新特性,支持在 key 中插入可变的$admin$

# demo 

Add 2 config keys :

```
base.skin_$admin$
    element type    : checkbox_group
    options :
    fixed
    layout-boxed
    layout-top-nav
    sidebar-collapse
    sidebar-mini

base.layout_$admin$
    element type    : radiobox_group
    options :
        skin-blue
        skin-blue-light
        skin-yellow
        skin-yellow-light
        skin-green
        skin-green-light
        skin-purple
        skin-purple-light
        skin-red
        skin-red-light
        skin-black
        skin-black-light
```

Then add some codes at `Admin/bootstrap.php` :

```php
config(
    [
        'admin.skin' => config('base.skin_admin_' . Admin::user()->id, 'skin-blue'),
        'admin.layout' => explode(',', config('base.layout_admin_' . Admin::user()->id, 'fixed')),
    ]
);
```