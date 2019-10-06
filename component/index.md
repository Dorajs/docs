# 组件 (component)

每个组件对应的是一个原生页面，每次打开一个新页面时就会创建一个新的组件。
每个组件文件需要通过 `module.exports` 指定一个 `object`。
举个栗子：
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
组件实例化后会拥有以下基础成员：
- `id: string` 资源标识
- `title: string` 标题
- `subtitle: string?` 子标题
- `link: string?` 资源的原网页 URL
- `thumb: string?` 缩略图地址
- `args: object readonly`: 当前路由的参数，只读
- `const type: string` 组件的类型，具体支持的类型列表下面会详细列出，__无法动态修改__
- `menus: []?`: 菜单列表，每个组件可以指定菜单
- `fetch(): object` 组件初始化时会执行这个方法来获得组件的数据
- `refresh()` 刷新页面（重新加载数据）

## `type`
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


## `fetch(): object`

Dora 扩展的组件是通过 `fetch()` 方法来初始化页面数据的，它返回一个 object，之后 Dora 会把这个 object 的属性值赋值给组件的相应成员属性。

```javascript
module.exports = {
    async fetch() {
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
    fetch () {
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
    fetch () {
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
    async fetch () {
        let res = await $http.get(`https://my-api/posts/${this.args.id}`)
        return { url: res.data.url }
    }
}
```
> [!TIP]
> 组件的成员属性值会自动从点击时的列表元素数据继承下来
