# $input
> 用户输入操作

## confirm(data: object): Promise<boolean>
让用户确认一个操作，支持参数：
 - `title: string`: 标题
 - `message: string`: 文本消息
 - `okBtn: string|null`: 确定按钮的文字，默认为“确定”

返回一个 `Promise<boolean>`，值表示用户是否点了确定按钮

```javascript
let ok = await $input.confirm({
  title: 'Confirmation',
  message: 'Are you sure?',
  okBtn: 'okBtn'
})
$ui.toast(`ok=${ok}`)
```

## text(data: object): Promise<boolean>

输入文本，支持参数：
 - `title: string`: 标题
 - `hint: string|null`: 输入提示
 - `value: string|null`: 默认值
 - `okBtn: string|null`: 确定按钮的文字，默认为“确定”

返回一个 `Promise<string|null>`，值为用户输入的内容，null 表示用户取消了输入
```javascript
let name = await $input.prompt({
  title: 'Dora.js prompt',
  hint: 'Input your name',
  value: ''
})
$ui.toast(`Hello ${name}`)
```

## number(data: object): Promise<boolean>

输入数字，输入法以数字方式打开，支持参数：
 - `title: string`: 标题
 - `hint: string|null`: 输入提示
 - `value: number|null`: 默认值
 - `okBtn: string|null`: 确定按钮的文字，默认为“确定”

返回一个 `Promise<number|null>`，值为用户输入的内容，null 表示用户取消了输入
```javascript
let name = await $input.number({
  title: 'input your age',
  hint: 'age'
})
$ui.toast(`age:${name}`)
```

## password(data: object): Promise<boolean>

输入密码，在运行时输入法以密码的方式打开，支持参数：
 - `title: string`: 标题
 - `hint: string|null`: 输入提示
 - `value: string|null`: 默认值
 - `okBtn: string|null`: 确定按钮的文字，默认为“确定”

返回一个 `Promise<string|null>`，值为用户输入的内容，null 表示用户取消了输入

```javascript
let name = await $input.number({
  title: 'input password',
  hint: 'password'
})
$ui.toast(`age:${name}`)
```

## select(data: object): Promise<object|null>
用于弹窗向用户提供一个选择窗口，可以实现单选和多选，输入参数：
 - `ttitleitle: string`: 标题
 - `multiple: boolean`: 是否支持多选，默认为 false
 - `options: object[]`: 选项列表，`title: string` 属性会用于显示
 - `okBtn: string|null`: 确定按钮的文字，默认为“确定”, `multiple` 为 true 才有效

返回一个 `Promise<object|null>`，值为用户选择的选项(`options` 中的条目), null 表示用户取消了选择
```javascript
let option = await $input.select({
  title: 'Dora.js select',
  multiple: true,
  options: [{
    id: 'option2',
    title: 'Option 1'
  }, {
    id: 'option2',
    title: 'Option 2'
  }]
})
$ui.toast(`Selected ${option.title}`)
```

## prompt(data: object): Promise<boolean>

>[TIP!]本接口在最新版本已经被 $input.text() 代替，本接口文档不再更新

输入文本，支持参数：
 - `title: string`: 标题
 - `hint: string|null`: 输入提示
 - `value: string|null`: 默认值
 - `okBtn: string|null`: 确定按钮的文字，默认为“确定”

返回一个 `Promise<string|null>`，值为用户输入的内容，null 表示用户取消了输入

```javascript
let name = await $input.prompt({
  title: 'Dora.js prompt',
  hint: 'Input your name',
  value: ''
})
$ui.toast(`Hello ${name}`)
```