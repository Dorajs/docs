# folder 组件

目录组件，适合展示列表类的数据
  
```javascript
module.exports = {
  type: 'folder',
  style: 'simple'
  async fetch(page) {
    let resp = await $http.get(`http://api.example.com/data?page=${page || 1}`)
    return {
      nextPage : (page || 1)  + 1,
      items : resp.data.data.map(post => {
        title: post.title
      })
    }
  }
}
```
folder 的 `fetch()` 方法会有一个 `page` 的参数，表示要加载的是第几页，当为 `null` 的时候表示首次加载或者刷新。
除了基础的成员外，folder 组件的实例还有如下成员：
 - `style: string` 列表风格样式，有如下值可供选择：
  - top_tab
  - bottom_tab
  - drawer
  - simple
  - live
  - icon
  - gallery


`data` / `fetch()` 要求的数据类型：

  - `nextPage: any?` 下一页，可以是任意数据类型，这个值会传给接下来用于加载更多时 `fetch(page)` 方法，当为 null 时表示已经列表已经全部加载完成

  - `items: []` 列表的元素数组，当数量为 0 时表示列表已经全部加载完成
  
特别地，如果不需要分页加载，可以直接使用 `[...]`
```javascript
module.exports = {
  type: 'folder',
  style: 'simple'
  fetch(page) {
    return [{
        title: '推荐'
      }, {
        title: '分类'
      }
    ]
  }
}
```
items 数组元素是一个 object，要求的数据格式如下：
 - `id: string?` id 标识符
 - `title: string` 资源的标题
 - `summary: string?` 资源的简单描述
 - `viewerCount: number?` 观看数量
 - `commentCount: number?` 评论数量
 - `time: string?|integer?` 资源创建的时间，可以是数值型的 Unix 时间戳或者日期字符串
 - `thumb: string?|object?` 缩略图 / 图标，可以是一个网络图片的 URL 地址、图标、本地图片，如果需要指定其他属性，可以使用 object 类型，支持以下属性：
   - `url`: 图片地址
   - `color`: 主题色
   - `aspect`: 宽高比
 - `author: object?` 资源的作者
 - `onClick: string?` 点击后回调的方法名
 - `route: object?` 对应的路由，`onClick` 的优先级要比 `route` 高，如果 `onClick` 不为 null 则 `route` 的值会失效
 - `link: string?` 这个资源的原网页 URL 地址，如果不为 null 会有一个 “原网页” 的菜单项

数组中每个元素对象的属性除了 `title` 外都是可选的，你应该尽快能多的进行赋值，Dora 在显示的时候也是尽可能多的显示这些信息，如果某个属性为 null，相应的 UI 就会隐藏。
