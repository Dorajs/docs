# package.json 接口

## 更新内容

可以设置 `updates` 属性设置更新内容，这个更新内容在其他用户订阅账户后可以看到

## 搜索

可以在文件中使用 `contributes.search` 属性指定一个搜索门面

范例：

```javascript
module.exports={
    async fetch({page,args}){
        console.log(args.keyword)
    }
}

```