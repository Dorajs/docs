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
- `title: string` 标题
- `subtitle: string?` 子标题
- `args: object readonly`: 当前路由的参数，只读
- `const type: string` 组件的类型，具体支持的类型列表下面会详细列出，__无法动态修改__
- `menus: []?`: 菜单列表，每个组件可以指定菜单
- `data: any` 组件的数据，不同类型的组件会有不同的数据格式要求，如果需要初始化完成之后修改组件数据，可以对这个属性进行赋值。
- `fetch(): any` 组件初始化时会执行这个方法来获得组件的数据
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


## `fetch(): any`

每个组件都需要数据用来展示，组件的数据就是通过 `fetch()` 方法来获取的，Dora 允许你使用不同的方式来返回数据：
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
        return $http.get(`https://my-api/posts/${this.args.id}`)
        .then((res) => {
            return { url: res.data.url }
        })
    }
}
```
 - 向 `this.data`赋值
```javascript
module.exports = {
    fetch () {
        $http.get(`https://my-api/posts/${this.args.id}`)
        .then((res) => {
            this.data = { url: res.data.url }
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