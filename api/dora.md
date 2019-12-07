# $dora
> 可以获得 Dora.js 应用的一些信息，以及对扩展实例进行一些配置

## mixin(object)
为所有组件继承一个对象

例如，在所有组件 `created()` 时，打印一条日志：
```javascript
$dora.mixin({
    created() {
        console.log('component created')
    }
})
```

## defaultSearchRoute: Route
设置默认的搜索路由，会在所有页面上方显示一个搜索按钮
可通过 [$route](./route) 构建路由，建议在 [入口文件](/arch/tree#mainjs)中进行设置

## versionCode: number
获取 Dora.js 的版本号，如：`10`

## versionName: string
获取 Dora.js 的版本名，如：`1.0.0`