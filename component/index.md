# 组件 (component)

每个组件对应的是一个原生页面，每次打开一个新页面时就会创建一个新的组件。
每个组件文件需要通过 `module.exports` 指定一个 `object`。

例如 ：
```javascript
module.exports = {
    type: 'folder'
    async fetch() {
        val resp = await http.get('http://api.example.com/')
        val data = // process the data to adapt type data structure
        return data
    }
}
```
所有组件实例都有以下成员，不同组件可能会扩充其他成员：

| 成员 | 类型  | 默认值 | 自动继承 | 描述 |
| :--- | :---: | :----- |: -------|:-------|
| type        | `const string` | `folder`    |   | 组件的类型 ([详情](../component/index?id=type))，组件初始化后就不能再修改 |
| id        | `string` | `null`    | ✔️  | 标识 ID，用于区分资源 |
| title     | `string` | `null`    | ✔️  | 主标题 |
| subtitle  | `string` | `null`    |     | 子标题 |
| summary   | `string` | `null`    | ✔️  | 概要描述 |
| link      | `string`    | `null`    | ✔️  | 原网页 URL 地址，如果有值，页面会有一个“原网页”菜单项，点击打开原网页 |
| image     | `string/Image`  | `null` | ✔️  | 可以是缩略图或者图标等，接受一个 URL 地址或者 [Image](../api/struct?id=image) 对象|
| author    | `Author` | `null`    | ✔️  | 作者信息 ([详情](../api/struct?id=author)) |
| error     | `string` | `null`    |   | 出错信息，如果出现加载错误，可自定义错误的消息，否则 Dora 会把 Error 的 message 作为错误信息展示 |
| args      | `object` | `{}`      |      | 该组件路由的参数，由上一级目录组件传入，只读|
| menus      | `Menu[]` | `{}`     |      | 菜单项 ([详情](../component/index?id=menus))|
| fetch()   | 方法      |   n/a     |      | 用于初始化组件数据 ([详情](../component/index?id=fetch)) |
| refresh() | 方法      |   n/a     |      | 刷新当前组件，重新初始化组件数据 |

> [!TIP]
> “自动继承”的意思是这些属性值可以从点击时的列表元素属性继承下来，比如你是从一个 `title` 为 'Hello World' 的列表元素点击进入这个组件的，那么这个组件的 `title` 在初始化时候就会设置为 'Hello World'，这样可以简化很多冗余代码。

## `type`
> 组件类型

我们可以通过 `type` 来指定组件的类型，指定类型后会加载相应类型的 API，扩展组件实例化对象的成员，`type` 不指定情况下为 `folder`。
```javascript
module.exports = {
    type: 'video'
}
```
Dora 支持以下类型的组件：
 - __folder__: 目录组件，适合展示列表类的数据
 - __video__: 视频播放器组件
 - __audio__: 音频播放器组件
 - __article__: 文章查看组件
 - __image__: 图片查看组件
 - __book__: 图书查看组件 **❌暂未完善**
 - __cartoon__: 漫画查看组件 **❌暂未完善**
 - __compose__: 编辑器组件 **❌暂未完善**


## `fetch(context): object`
> 初始化组件数据

`fetch()` 方法接受一个 `context` 的参数，可以利用它来获取所需的一些参数，它拥有以下属性：
 - `from: Route`: 来源的路由
 - `route: Route`: 当前组件的路由
 - `args: object`: `route.args` 的别名
 - `page: any?`: 分页加载时用到的分页信息（目前只有 folder 类型的组件才会有这个值

> [!TIP]
> 为了方便我们可以利用 JavaScript 的 [解构赋值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#%E8%A7%A3%E6%9E%84%E5%AF%B9%E8%B1%A1) 来更方便的得到所需的参数:
> ```javascript
> module.exports = {
>    async fetch({ page, args }) {
>        // ...
>    }
> }
>```

`fetch()` 返回一个 object，之后 Dora 会把这个 object 的属性值赋值给组件的相应成员属性。

```javascript
module.exports = {
    async fetch({ args }) {
        let resp = await $http.get(`http://api.example.com/user/${args.uid}`)
        return {
            title: '', // 等同于 this.title = ''
            subtitle: '', // 等同于 this.subtitle = ''
            menus: [], // 等同于 this.menus = []
            // ...
        }
    }
}
```
Dora 允许你使用不同的方式来返回数据：
 - 直接返回数据，适合一些静态数据

```javascript
module.exports = {
    style: 'bottom_tab',
    fetch (conetxt) {
        return [{
            title: '推荐',
            route: $route.folder('recommend')
        }]
    }
}
```
 - 返回一个 `Promise`
```javascript
module.exports = {
    fetch (conetxt) {
        return $http.get(`https://api.example.com/posts/${this.args.id}`)
        .then((res) => {
            return { url: res.data.url }
        })
    }
}
```

 - (推荐)使用 `await/async` ([学习一下](https://javascript.info/async-await))
```javascript
module.exports = {
    async fetch (conetxt) {
        let res = await $http.get(`https://my-api/posts/${this.args.id}`)
        return { url: res.data.url }
    }
}
```