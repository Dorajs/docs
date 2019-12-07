# 入口文件

Dora.js 扩展的入口文件为 `main.js`，扩展在启动时首先会执行这个文件，每个扩展实例执行期间该文件只会执行一次，在该文件中 `module.exports` 返回的对象属性会放到全局对象(`global`)中，建议在入口文件中进行一些全局的初始化操作。

示例：
``` javascript
var _areas = null;
$dora.mixin({
    created() {
        console.log(this)
    }
})
$dora.searchRoute = route.folder('search', {})
module.exports = {
    endpoint: 'https://api.exmple.com/'
}
```
