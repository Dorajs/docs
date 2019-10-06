# 路由

Dora 使用路由的概念来进行目标组件的加载
```javascript
{
    // ...
    route: $route.folder('top', { id: 1})
    // ...
}
```
路由通过 `$route.xxx(component: string?, args: object?)` 来构建，`$route` 更详细的方法列表见: [$route](../modules/route)

如果 `component` 传入 null，会使用默认的组件实现，并且将 `args` 作为组件的数据：
```javascript
{
    title: 'video',
    route: $route.video(null, {
        url: 'http://devimages.apple.com.edgekey.net/streaming/examples/bipbop_16x9/gear5/prog_index.m3u8',
        thumb: 'https://goss.veer.com/creative/vcg/veer/800water/veer-310433275.jpg'
    })
}
```

`args` 是目标组件的参数，目标组件可以通过 `this.args` 取到这个值