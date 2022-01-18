# TODO

## 这里是没有写进文档里的更新

- 全局 url 资源均支持设置 http headers
- `package.json` 支持通过 `contributes.search` 设置用于全局搜索的组件
- 新增以下全局函数:
  - `$input.text()` （取代之前的 `$input.prompt()`）
  - `$input.number()`
  - `$input.password()`
- 扩展详情页支持更新和向作者捐赠
- 视频播放器在非全屏时可右滑关闭
- 添加“魔法分享”来分享扩展和 npm 用户
- “更多” 页添加“更新日志”
- 修改默认加速 npm 镜像地址为 "r.cnpmjs.org"
- 添加 `label`, `chips` 列表 (list) 组件样式
- `thumb` 字段统一改为 `image` (兼容 `thumb`)
- 支持设置捐赠方式
- 支持设置更新内容
- 新增以下全局函数：
  - `$ui.viewUser()`
  - `$ui.browser()`
  - `$dora.addons()`
  - `$dora.install()`
  - `$dora.uninstall()`
  - `$dora.isInstalled()`
  - `$dora.subscribe()`
  - `$dora.isSubscribed()`
## 1.0.2-beta (2019.12.15)
- 修复搜索按钮不生效的问题
- 修复部分闪退问题
- 修复 webview 组件 无法输入文件的问题
- audio/video 组件支持设置 headers 属性
- 修复很多闪退问题
- 支持非 64 位设备
- 默认仓库使用国内服务器地址（加速访问）
API：
- $route() 支持任意 schema url
