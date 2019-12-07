# 扩展包结构

Dora.js 的扩展包是以 `.dora` 为后缀，本质上只是一个 `tar.gz` 压缩文件，扩展包的目录结构如下：

```
├── assets/
    ├── icon.xxx
    ├── prefs.json
├── components/
    ├── index.js
├── scripts/
├── main.js
└── package.json
```
## `assets/`
存放扩展的资源，如图片、数据文件等

## `components/`
存放组件文件的目录，每个组件对应一个原生的页面，组件可能会被执行多次

## `scripts/`
存放一些脚本文件，如注入到 WebView 中的 js 脚本

## `prefs.json`
扩展的自定义配置，通过简单的 json 配置，即可生成一个美观、方便的原生配置界面

详细格式请见 [配置项](arch/prefs)

## `icon.xxx`
扩展的图标，可以有不同的后缀，如：`.png`、`.jpg`、`.webp`、`svg`

## `main.js`
入口文件，启动扩展时首先会执行这个文件，可以进行一些全局初始化工作

详细描述见 [入口文件](arch/main)

## `package.json`
包含扩展的名称、版本号、作者、依赖等信息