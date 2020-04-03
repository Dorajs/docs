# drawer 组件
> 显示一个抽屉菜单

drawer 组件额外支持设置以下属性：
 - `items: object[]`: 抽屉菜单中的选项

示例：

```javascript
module.exports = {
  type: 'drawer',
  fetch() {
    return [{
      title: '电影',
      image: $icon('movie'),
      route: $route('movies')
    }, {
      title: '电视剧',
      image: $icon('tv'),
      route: $route('soap')
    }]
  }
}
```