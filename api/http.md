# $http
> 进行 http 网络请求

Dora 运行时集成了著名的网络请求库 [axios](https://github.com/axios/axios)，`$http` 只是它的一个别名，除此之外没有任何其他区别。

因为 axios 已经有非常好的文档了，本文档就不再详细说明，具体可参见 [axios 官方文档](https://github.com/axios/axios)，使用时将官方文档中的 `axios` 替换为 `$http` 即可，这里会举一些常见的例子供大家快速上手，读者也可以查看 [Dora 官方扩展仓库](https://github.com/DoraKit/addons) 中的示例来学习。

## 获取 json
```javascript
module.export {
    async fetch() {
        let resp = await $http.get('https://api.example.com/')
        console.log(resp.data)
    }
}
```

## 提交表单请求
```javascript
module.export {
    async fetch() {
        let resp = await $http.post('/user', {
            firstName: 'Fred',
            lastName: 'Flintstone'
        })
        console.log(resp.data)
    }
}
```