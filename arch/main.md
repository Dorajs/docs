# 入口文件

Dora 扩展的入口文件为 `main.js`，扩展在启动时首先会执行这个文件，每个扩展实例执行期间该文件只会执行一次，在该文件中，通过 `module.exports` 返回的对象属性会放到全局对象(`global`)中。

示例：
``` javascript
var _areas = null;
Dora.mixin({
    async getAreas() {
        if (_areas === null) {
            const response = await http.get(`${endpoint}/v1/Area/getList`);
            _areas = response.data.data;
            return _areas;
        }
        return _areas;
    },
    created() {
        console.log(this)
    }
})
module.exports = {
    endpoint: 'https://api.live.bilibili.com/room'
}
Dora.searchRoute = route.folder('search', '搜索', {})
```