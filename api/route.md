# $route
> 用于构建路由 (Route) 对象

## `$route(path:string, arg: object)`

参数：
 - `path: string?` 组件路径，相对于 `components` 文件夹的路径，如 `components/posts/index.js` 文件的 path 应为 `posts/index`
 - `args: object` 路由参数，默认 `{}`

> [!TIP]
> 可以使用默认的组件实现，它把路由的 `args` 作为 `fetch()` 的返回值
> 默认组件的 fetch() 实现如下：
>```javascript
> fetch({ args }) {
>     return args
> }
>```
