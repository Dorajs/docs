# video 组件

video 类型所需的数据结构如下：
```javascript
{
    id: '...', // string?，资源 ID，可用于 Dora 进度恢复，否则 Dora 会使用 url 作为进度恢复的标识
    url: 'http://...', // string，视频地址
    link: 'http://...', // string，原网页地址
    thumb: 'http://....', // string?, 缩略图地址
    title: 'http://....' // string?, 标题
}
```
> 这些属性默认会从点击时的列表元素数据继承下来

除了基础的成员外，folder 组件的实例还有如下成员：
  - `selectors[]`
如果视频有不同的线路或者不同的清晰度，可以通过 `selectors` 来进行设置，它接受一个数组，数组元素的数据结构如下：

```javascript
{
    id: 'quiality',      // 这个 selector 的 id，可以标识不同的 selector
    options: [{
        title: '高清', // 选项显示的标题
        args: {       // 选项的参数
            // ... 
        }
    },
    ....
    ]
}
 ```