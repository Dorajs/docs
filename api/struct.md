# 通用数据结构
> 这些数据结构在多个地方会用到，统一在这里详细说明他们的属性

## `Author`
用来描述资源的作者信息，有以下属性:
- `name: string` 作者姓名
- `avatar:string?` 作者头像 URL 地址
- `route: string?` 用户点击作者头像/姓名时跳转的路由


## `Image`
用来描述图片资源，可以是图标、本地图片、网络图片，有以下属性：
 - `url: string`: 图片地址
 - `width: number?`: 图片宽度
 - `height: number?`: 图片高度
 - `color: string`: 图片的主题色，使用 16 进制并且以 `#` 开头，如: `#FFFFFF`, `#000000`

> [!TIP]
> 由于许多时候我们图片我们只需要一个 URL，所以所有用接受 `Image` 的地方也都可以接受一个 `string` 类型的 URL 地址。
> 另外，你可以使用 [`$icon(name[, color])`](./icon) 返回一个预设的图标地址, 使用 [`$assets(path)`](./assets) 返回一个本地图片资源地址

## `Route`
用来描述路由信息，路由可用来不同组件之间跳转，有以下属性：
 - `type: string`: 组件的[类型](/component/index#type)
 - `path: string`: 组件的路径，这个文件路径是相对于 `components/` 目录，如你的组件文件是 `components/user/profile.js`，那么 `path` 只需要填 `user/profile`
 - `args: object`: 传入的参数

> [!TIP]
> Dora.js 提供了 [`$route`](./route) 来让你方便的创建 `Route`