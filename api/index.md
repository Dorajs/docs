# 全局 API

Dora 内置了许多全局(global) API 可供调用，为了避免命名冲突，这些 API 都是以 `$` 开头。

 - `$dora` 可以获得 Dora 应用的一些信息，以及对扩展实例进行一些配置
 - `$http` 网络请求
 - `$route` 构建路由对象
 - `$ui` 一些方便简单的 UI 交互
 - `$prefs` 读取和设置配置项
 - `$storage` key-value 的本地数据存储
 - `$debugger` 用于调试的一些方法