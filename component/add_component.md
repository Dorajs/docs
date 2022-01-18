# 添加一个组件

当扩展创建好后，Dora.js 已经自动创建了一个组件文件: `components/index.js`
如果需要新增页面，就需要创建一个新的组件文件了，

## 在 Dora.js 中

通过面包屑图标打开抽屉菜单 -> 点击 "components" 文件夹 -> 点击 “+” 图标按钮 -> 添加文件 -> 输入文件名

![Add component](../_media/add_component.gif ':size=400')

## 在 VSCode 中

在 `components/` 目录下添加 js 文件，并添加如下代码：

```javascript
module.exports = {
  type: 'list',
  async fetch() {
    // ...
  }
}
```