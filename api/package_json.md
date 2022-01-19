# package.json 接口

## 更新内容

## 搜索

可以在文件中使用 contributes.search 属性指定一个搜索门面

范例：

```javascript
module.exports={
    async fetch({page,args}){
        console.log(args.keyword)
    }
}

```