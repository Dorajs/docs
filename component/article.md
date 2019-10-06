# audio 组件

audio 类型所需的数据结构如下：
```javascript
{
    id: '...', // string?，资源 ID，可用于 Dora 进度恢复，否则 Dora 会使用 url 作为进度恢复的标识
    url: 'http://...', // string, 文章的 URL 地址
    link: 'http://...', // string, 原网页地址
    thumb: 'http://....', // string?, 缩略图地址
    title: 'http://....' // string?, 标题
    content: '...' // string?, 文章的内容，可以是 html 或者纯文本，如果 `content` 为 null 会使用 url 加载网页
}
```
> 这些属性默认会从点击时的列表元素数据继承下来
