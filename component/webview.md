# webview 组件
> 可用于打开一个网页，支持获取 Cookie、执行 js 脚本等


webview 组件额外支持设置以下属性：
 - `url: Url`: 要打开的网页地址
 - `script: string|null`: 要打开的网页地址
 - `onPageFinished(url: string)`: 网页加载完成的回调
 - `onPageStarted(url: string)`: 网页开始加载时的回调
 - `onLoadingUrl(url: string)`: 正在加载中的资源 url
 - `onEvent(name: string, data: any)`: 从网页发送过来的事件
 - `uiOptions: object`: 设置系统栏显示选项
  - `statusBar: boolean`: 是否显示状态栏
  - `toolBar: boolean`: 是否显示顶部操作栏
  - `navigationBar: boolean`: 是否显示底部导航栏

webview 组件额外提供以下接口：
  - `runScript(script: string)`: 在网页中执行 JS 代码，`script` 可以是 JS 代码也可以是 `scripts/` 目录下的 js 文件
  - `redirect(url: Url)`: 跳转到指定 url
  - `cookies: object`: 获取 / 设置当前网页的 cookie，获取时会得到全部 cookie，赋值时会和已经存在的 cookie 作合并操作


## 通信

网页运行的 JS 和 组件是两个不同的运行时，彼此交互需要进行通信:

 - 网页 -> 组件:
  可通过 `$dora.sendEvent(name: string, data: any)` 来发送事件到组件中，在组件中通过 `onEvent(name: string, data: any)` 来接收

 - 组件 -> 网页:
  使用 `this.runScript()` 执行脚本即可
