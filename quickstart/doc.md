# 文档说明

此文档托管在 [Dorajs/docs](https://github.com/Dorajs/docs)，如果你有任何建议或疑问，欢迎到 [issues](https://github.com/Dorajs/docs/issues) 中提出来，如果你能提交 PR 来优化这个文档就更好了！

## 数据类型
本文档中在描述数据类型时，参考 typescript 中的类型声明

- 变量: `const name: type|null`
 - `const` 表示这个变量是常量，无法修改
 - `name` 是这个变量的名称
 - `type` 是这个变量的类型
 - `|null` 表示这个变量不是必选，值可以为 null

 例子: 
  - `title: string` 变量名为 title，类型是 `string`
  - `action: Action|null` 变量名为 action，类型是 `Action`，可为 null
  - `const type: string` 变量名为 type，类型是 `string`，常量不可修改
  - `items: Item[]` 变量名为 items，`Item` 数组

- 函数: `foo(arg1: type...): type`
  - `foo` 表示函数名
  - `arg1: type...` 表示函数的参数列表
  - `: type` 返回类型

 例子: `fetch(context: object): object`
