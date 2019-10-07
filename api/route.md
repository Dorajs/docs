# $route
> 用于构建路由 (Route) 对象

`$route` 包含所有的组件类型名的方法，：
 - folder(path, args): Route
 - video(path, args): Route
 - audio(path, args): Route
 - image(path, args): Route
 - article(path, args): Route

参数：
 - `path: string?` 组件路径，如果 path 为 null，则会使用默认的组件实现，并且把 `args` 作为默认组件的数据使用
 - `args: object?` 路由参数

额外的，如果想使用其他 App 打开一个 URL 可以使用 `$route.url(url, args): Route`

参数：
 - `url: string` URL 地址
 - `args: object?` 会转化为 URL 的 query 参数