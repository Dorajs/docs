# 全局 API

Dora.js 内置了许多全局(global) API 可供调用，为了避免命名冲突，这些 API 都是以 `$` 开头，你可以在直接使用无需 `require(...)`。

 - `$dora` 可以获得 Dora.js 应用的一些信息，以及对扩展实例进行一些配置 ([详情](api/dora))
 - `$http` 网络请求 ([详情](api/http))
 - `$ui` 一些方便简单的 UI 交互 ([详情](api/ui))
 - `$input` 输入操作 ([详情](api/input))
 - `$router` 路由导航 ([详情](api/router))
 - `$prefs` 读取和设置配置项 ([详情](api/prefs))
 - `$storage` key-value 的本地数据存储( [详情](api/storage))



以下全局方法也可以直接使用：
## $route(path: string, args: object): Route
> 构建组件路由 (Route) 对象

 - `path: string`: 组件路径，相对于 `components` 文件夹的路径，如 `components/posts/index.js` 文件的 path 应为 `posts/index`
 - `args: object`: 路由参数，默认 `{}`

> [!TIP]
> 可以使用默认的组件实现，格式为在组件类型名前面加上 `@`，如：`$route('@image', { url: ... })`，它会把路由的 `args` 作为 `fetch()` 的返回值，我们来看看默认组件实现的 fetch() 方法源码：
>```javascript
> fetch({ args }) {
>     return args
> }
>```

## $icon(name: string, color: string|null): Url

> 创建一个内置的图标 Url

- `name: string`：图标名称

 请使用官方仓库中的 API Demo 中查看 Dora.js 内置的所有图标，Dora.js [内置了 Material Desin Icon](https://github.com/google/material-design-icons)

- `color: string|null`: 图标的颜色

 可以是 `#` 开头的16进制颜色值，也可以使用预置的语义化值：black, darkgray, gray, lightgray, white,  red, green, blue, yellow, cyan, magenta, aqua, fuchsia, darkgrey, grey, lightgrey, lime, maroon, navy, olive, purple, silver, teal

```javascript
$icon('ic_settings')
$icon('ic_settings', 'black') // with black color
```

## $assets(path: string): Route
> 创建一个 `assets` 目录下的资源 Url

 - `path: string`: 资源路径，相对于 `assets` 文件夹的路径，如 `assets/cities.json` 文件的 path 应为 `cities.json`

```javascript
$assets('cities.json')
```