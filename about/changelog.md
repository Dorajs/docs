# Changelog

## 1.8.1-beta (2020.4.27)
- 创建扩展时自动生成一个图标文件
- 优化竖屏视频播放体验
- 视频播放组件支持查看视频地址
- 优化分享扩展时的文件名
- 修复全屏时小窗状态不对的问题
- 修复在扩展详情页升级后扩展无法运行的问题
- 修复若干闪退和体验问题

API:
- 新增 `$permission.request()` 申请权限，目前只支持申请 'sdcard'

## 1.7.0-beta (2020.4.19)
- 👍 更好的小窗体验
- 修复视频组件切换内容后弹幕未结束的问题
- 修复直播视频显示滑动条的问题
- 修复嵌套组件显示问题

API:
- 添加 `$storage.remove()`
- 修复组件 `this.finish()` 无法调用的问题
- 修复组件生命周期钩子调用问题
- 列表组件添加 `dashboard` 样式

## 1.6.1-beta (2020.4.13)
- 🔥 支持全局搜索
- 支持使用外部播放器打开视频
- 优化编辑器依赖下载速度
- 最低支持到 Android 6.0
- 使用 64 位 native 库
- 修复手动输入 id 无法安装扩展的问题
- 修复安装其他扩展时会导致当前扩展重新加载的问题
- 若干细节优化和闪退问题修复

API：
- 添加 `richContent` 列表 (list) 组件样式
- 全局 url 资源均支持设置 http headers
- `package.json` 支持通过 `contributes.search` 设置用于全局搜索的组件
- 新增以下全局函数:
  - `$input.text()` （取代之前的 `$input.prompt()`）
  - `$input.number()`
  - `$input.password()`

## 1.5.1-beta (2020.4.6)
- 扩展详情页支持更新和向作者捐赠
- 视频播放器在非全屏时可右滑关闭
- 添加“魔法分享”来分享扩展和 npm 用户
- “更多” 页添加“更新日志”
- 修改默认加速 npm 镜像地址为 "r.cnpmjs.org"
- 修复版本号比较问题
- 修复部分闪退问题
- 修复若干体验问题

API：
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

vscode 插件：
-  不再依赖 yarn
-  支持同步扩展文件到当前目录
-  添加覆盖文件确认

## 1.4.0-beta (2020.4.2)

- __升级 Node.js 到最新版本 (14.0.0-pre) __
- 扩展列表支持按“最近”、“常用排序
- 添加页面过渡动画

## 1.3.0-beta (2020.3.21)

- 添加扩展详情页
- 添加 npm 用户详情页
- 优化订阅的扩展包同步速度
- 修复各种体验问题
- 添加支持扩展、订阅等管理 API

## 1.2.4-beta (2020.3.3)

- 修复无法获取新发布的扩展包问题
- 支持分享订阅 (npm 用户), 复制后打开应用自动识别
- 修复严重的闪退问题
- 修复编辑器查找&替换显示问题
- 修复编辑器点击时无法自动滚动聚焦的问题

## 1.2.1-beta (2020.3.2)

- 极大增强了编辑器：支持智能补全、显示方法签名、显示上下文信息等等，添加了非常多的工具
- 扩展仓库改为了订阅 npm 用户的方式
- 扩展加入了分类属性

## 1.1.2-beta (2020.1.7)

- 支持使用手机热点连接 VSCode
- 修复编辑器宽度问题
- 修复若干闪退问题
- 修复短时间按住扩展松开时启动了扩展并打开了编辑器的问题

##  1.1.1-beta (2019.12.21)

- 格式化代码使用 prettier
- 优化编辑器横向滑动
- 添加 TG 群链接
- 修复 headers 设置部分属性失败的问题
- 修复部分闪退问题

## 1.0.2-beta (2019.12.15)
- 修复搜索按钮不生效的问题
- 修复部分闪退问题
- 修复 webview 组件 无法输入文件的问题

API：

- audio/video 组件支持设置 headers 属性

## 1.0.1-beta(2019.12.12)

- 修复很多闪退问题
- 支持非 64 位设备
- 默认仓库使用国内服务器地址（加速访问）

API：

- $route() 支持任意 schema url
