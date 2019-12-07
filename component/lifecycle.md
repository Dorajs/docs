 # 生命周期
同 [`Vue` 的组件](https://cn.vuejs.org/v2/guide/instance.html#%E5%AE%9E%E4%BE%8B%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E9%92%A9%E5%AD%90)一样，Dora.js 的组件也有生命周期，如组件实例化、获取数据、前后台切换、数据刷新等，在这些过程中也会运行一些叫做 __生命周期钩子__ 的方法，这给了用户在不同阶段添加自己的代码的机会。
例如，你可以在数据初始化之前修改页面的标题：
```javascript
module.exports = {
    beforeCreate() {
        this.title = 'Hello World'
    }
}
```
Dora.js 的组件拥有以下生命周期钩子函数：

 - `beforeCreate()` 组件获取数据之前，在 `fetch()` 方法执行之前
 - `created()` 组件已获取数据，在 `fetch()` 方法执行完成之后
 - `activated()` 页面可见（当前页面处于前台）
 - `updated()` 页面数据更新
 - `inactivated()` 页面不可见（应用退到后台，或者打开了新的页面）
 - `beforeDestroy()` 组件销毁之前
 - `destroyed()` 组件已销毁