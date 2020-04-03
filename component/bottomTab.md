# bottomTab 组件
> 底部 tab 组件

bottomTab 组件额外支持设置以下属性：
 - `items: object[]`: 底部的 tab，最大支持支 5 个，多余的不会被显示出来

示例：

```javascript
module.exports = {
  type: 'bottomTab',
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