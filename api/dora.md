# $dora
> 可以获得 Dora.js 应用的一些信息，以及对扩展实例进行一些配置，部分接口已经在最新版本被增加，如果无法使用，请考虑使用最新版本的 Dora.js

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
## addons():Promise<Addon[]>

- 用途：获取所有已经安装的插件列表
- 返回：Promise 对象
    - 如果成功，返回一个数组，里面包括所有安装的插件列表

## install(url:String):Promise<Addon|null>

 - 参数：一个插件的安装 URL，例如 `npm://@dora.js/unsplash`
 - 用途：安装一个扩展
 - 返回：Promise 对象
    - 订阅成功返回 True

## uninstall(uuid:String):boolean

- 参数：一个插件的 uuid
- 用途：卸载一个插件
- 返回：返回一个布尔值，卸载完成返回 True

## isInstalled(uuid:String):boolean

- 参数：一个插件的 uuid
- 用途：查找是否已经安装了某个插件
- 返回：返回一个布尔值，已经安装返回 True

## subscribe(userid:String):Promise<boolean>

- 参数：一个开发者的 userid
- 用途：订阅一个开发者
- 返回：Promise 对象
    - 如果成功，用户同意安装，返回插件的对象，否则返回空

## isSubscribed(userid:String):boolean

- 参数：一个开发者的 userid
- 用途：检查是否已经订阅了这个开发者
- 返回：返回一个布尔值，已经订阅返回 True

## versionCode: number
获取 Dora.js 的版本号，如：`10`

## versionName: string
获取 Dora.js 的版本名，如：`1.0.0`
