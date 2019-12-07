# list 组件
> 适合展示列表类的数据

![list type component](../_media/list_component.webp ':size=400')

除了基础的成员外，list 组件的实例还有如下成员：
 - `nextPage: any?` 下一页参数
 - `page: any?` 当前页参数
 - `items: object[]` 列表的条目数组
 - `append(items: object[])` 方法，往列表数据中添加条目
  
```javascript
module.exports = {
  type: 'list',
  style: 'simple'
  async fetch({ args, page }) {
    let resp = await $http.get(`http://api.example.com/data?page=${page || 1}`)
    return {
      nextPage : (page || 1)  + 1,
      items : resp.data.data.map(post => {
        title: post.title,
        style: 'simple'
      })
    }
  }
}
```
## 分页加载

由于列表数据需要进行分页加载，可们可以通过 fetch 方法的 `context` 参数来拿到要加载的分页参数，它的值其实等于 `this.nextPage`，当为 `null` 的时候表示首次加载或者刷新。  

- 访问 `context` 方式拿到
```javascript
  module.exports = {
      type: 'list',
      fetch(context) {
          console.log(context.page)
      }
  }
```
- 解构赋值方式拿到
```javascript
  module.exports = {
      type: 'list',
      fetch({ args, page }) {
          console.log(page)
      }
  }
```
在加载更多时 `fetch` 返回的 `items` 会自动追加到已有的 `items` 数组，而不是直接赋值。

> [!TIP]
> 如果不需要分页加载以及初始化组件其他属性，list 组件的 fetch 方法可以直接返回一个数组：
> ```javascript
> module.exports = {
>     fetch() {
>         return [ ... ]
>     }
> }
> ```

## items[]
`items` 是一个数组，数组元素 object 类型，Dora.js 内置了很多列表条目的样式，每个条目要求的数据属性不一样，这里我们列出列表条目数支持的所有属性：
 - `id: string` id 标识符
 - `title: string` 资源的标题
 - `style: string` 列表条目的样式，默认为 `simple` 目前支持一下值：
  - simple
  - live
  - icon
  - gallery
  - article
  - richMedia
  - category
  - vod
  - book
 - `spanCount: number` 列表条目所占的网格数 [详情](#spanCount)
 - `summary: string` 资源的简单描述
 - `viewerCount: number` 观看数量
 - `commentCount: number` 评论数量
 - `voteCount: number` 评分数量
 - `time: string|number` 资源创建的时间，可以是数值型的 Unix 时间戳或者日期字符串
 - `image: Url` 图片，更多[详情](api/struct#image)
 - `author: Author` 资源的作者([详情](api/struct#author))
 - `onClick: function` 点击后回调的方法
 - `onLongClick: function` 长按后回调的方法
 - `route: Route` 对应的路由，`onClick` 的优先级要比 `route` 高，如果 `onClick` 不为 null 则 `route` 的值会失效，更多[详情](../api/struct?id=route)

每个属性几乎都是可选的，你应该尽快能多的进行赋值，Dora.js 在显示的时候也是尽可能多的显示这些信息，不同 `style` 的列表条目需要的属性会有所不同，如果某个属性为 null，相应的 UI 就会隐藏。

## spanCount
 
 类似于 Bootstrap，Dora.js 列表将横向空间划分为了 12 份，通过 `spanCount` 来指定一个条目占多大比例，所有样式的条目都有不同默认的值，你可以通过设置列表条目的 `spanCount` 属性来更改这个值。
 ![spanCount](../_media/spanCount.png)

## 列表条目样式
 - simple

  spanCount 默认值: 12

  ![Simple style](../_media/simple_style.png)

 - icon

  spanCount 默认值: 4

  ![icon style](../_media/icon_style.png)

 - vod

  spanCount 默认值: 6

  ![vod style](../_media/vod_style.png)

 - live

  spanCount 默认值: 6
  
  ![live style](../_media/live_style.png)