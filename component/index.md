# 组件

每个组件文件对应的是一个原生页面，每次打开一个新页面时就会创建一个新的组件 object，不同组件实例之间独立。
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
- `type` 指定组件的类型，类型列表下面会列出，__无法动态修改__
- `data` 组件的数据，不同类型的组件会有不同的数据格式要求，如果需要初始化完成之后修改组件数据，可以对这个属性进行赋值。
- `actions`: 菜单列表，每个组件可以指定菜单
- `fetch()` 组件初始化时会执行的方法，如果使用 `async/await`需要返回和 `data` 一致的数据结构

## 类型
我们可以通过 `type` 来指定组件的类型，指定类型后会加载相应类型的 mixin，也会有不同的原生 API 提供，默认为 `folder`
```javascript
module.exports = {
    props: {
        type: 'video'
    }
}
```
- folder
  
  `folder` 类型的数据会显示成列表，我们可以通过 `view` 指定列表的样式：
  - top_bar
  - bottom_bar
  - drawer
  - simple_list
  - live_list
  - icon_list
  - gallery

  folder 的 `fetch()` 方法会有一个 `page` 的参数，表示要加载的是第几页，当为 `null` 的时候表示首次加载或者刷新。
  
  folder 需要的数据结构如下：
  ```javascript
  {
    nextPage: page + 1,
    items: [...]
  }
  ```
  `nextPage` 表示下一页，可以是一个整数或者一个 object，当为 `null` 或者未指定的时候表示页面已加载完成。
  `items` 是一个数组，数组元素的数据结构如下：

  
- video
  
  video 类型所需的数据结构如下：
  ```javascript
  {
      url: 'https://example.com/video.flv', // 视频流地址
      is_live: true // 是否是直播流
  }
  ```
  - `this.selectors`
如果视频有不同的线路或者不同的清晰度，可以通过 `selectors` 来进行设置，它接受一个数组，数组元素的数据结构如下：
 ```javascript
 {
     id: 'quiality',      // 这个 selector 的 id，可以标识不同的 selector
     options: [
         {
            title: '高清', // 选项显示的标题
            args: {       // 选项的参数
                // ... 
            }
         },
         ....
     ]
 }
 ```

  - `this.addDanmu()`
  
- image

- article
  
## 生命周期
 - `beforeCreate()`
 - `created()`
 - `activated()`
 - `inactivated()`
 - `beforeDestroy()`
 - `destroyed()`