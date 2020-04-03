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

## versionCode: number
获取 Dora.js 的版本号，如：`10`

## versionName: string
获取 Dora.js 的版本名，如：`1.0.0`
