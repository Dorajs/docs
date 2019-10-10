# $route
> 用于构建组件路由 (Route) 对象

## `$route(path: string, arg: object)`

参数：
 - `path: string` 组件路径，相对于 `components` 文件夹的路径，如 `components/posts/index.js` 文件的 path 应为 `posts/index`
 - `args: object` 路由参数，默认 `{}`

> [!TIP]
> 可以使用默认的组件实现，格式为在组件类型名前面加上 `@`，如：`$route('@image', { url: ... })`，它会把路由的 `args` 作为 `fetch()` 的返回值，我们来看看默认组件实现的 fetch() 方法源码：
>```javascript
> fetch({ args }) {
>     return args
> }
>```
