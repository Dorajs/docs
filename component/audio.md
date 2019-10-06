# audio 组件

audio 类型所需的数据结构如下：
```javascript
{
    id: '...', // string?，资源 ID，可用于 Dora 进度恢复，否则 Dora 会使用 url 作为进度恢复的标识
    url: 'http://...', // string, 音频地址
    link: 'http://...', // string?, 原网页地址
    thumb: 'http://....', // string?, 缩略图地址
    title: 'http://....' // string?, 标题
}
```
> 这些属性默认会从点击时的列表元素数据继承下来
