# 通用数据结构
> 这些数据结构在多个地方会用到，统一在这里详细说明他们的属性

## `Author`
用来描述资源的作者信息，有以下属性:
- `name: string` 作者姓名
- `avatar:string?` 作者头像 URL 地址
- `route: string?` 用户点击作者头像/姓名时跳转的路由

## `Action`
支持点击操作的 菜单项/按钮
- `title: string` 标题
- `onClick: function|null` 点击时的回调
- `route: string?` 用户时跳转的路由
- `icon: url|null` 图标

## `Url`
用于描述资源地址，可以是：
 - 网络地址: https://example.com/icon.png
 - Dora.js 内置的资源: `$icon(name[, color])` ([详情](api/index))
 - 扩展包 assets 目录的资源: `$assets(path)` ([详情](api/index))

## `Route`
用来描述路由信息，路由可用来不同组件之间跳转，有以下属性：
 - `type: string`: 组件的[类型](/component/index#type)
 - `path: string`: 组件的路径，这个文件路径是相对于 `components/` 目录，如你的组件文件是 `components/user/profile.js`，那么 `path` 只需要填 `user/profile`
 - `args: object`: 传入的参数

> [!TIP]
> Dora.js 提供了 [`$route`](./route) 来让你方便的创建 `Route`