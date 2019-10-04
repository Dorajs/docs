# 框架设计

当你通过 Dora App 创建一个扩展后，会创建以下文件

```
├── components
│   ├── index.js
├── config.json
├── icon.png
├── main.js
└── package.json
```

## `components/` 目录
存放组件文件的目录，每个组件对应一个原生的页面，组件可能会被执行多次

## `config.json` 文件
扩展的自定义配置，通过简单的 json 配置，即可生成一个美观、方便的原生配置界面

详细格式请见 [配置项](config)

## `icon.png` 文件
扩展的图标，目前目前仅支持 png 格式

## `main.js` 文件
入口文件，启动扩展时首先会执行这个文件，可以进行一些全局初始化工作

详细描述见 [入口文件](main)

## `package.json` 文件
包含扩展的名称、版本号、作者、依赖等信息