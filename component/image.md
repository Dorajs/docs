# image 组件

image 类型所需的数据结构如下：
```javascript
{
    id: '...', // string?，资源 ID
    url: 'http://...', // string，图片的地址
    link: 'http://...', // string?, 原网页地址
    thumb: 'http://....', // string?, 缩略图地址
    title: 'http://....' // string?, 标题
}
```
> 这些属性默认会从点击时的列表元素数据继承下来
