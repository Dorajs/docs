# 配置项

你只需要在扩展根目录配置一个 `prefs.json` 文件，Dora.js 就可以自动生成一个友好的配置页面。

```json
{
    "name": {
        "type": "string",
        "default": "unkown",
        "title": "姓名"
    },
    "age": {
        "type": "number",
        "default": 0,
        "title": "年龄"
    },
    "show_recommend": {
        "type": "boolean",
        "default": true,
        "title": "是否显示推荐"
    },
    "password": {
        "type": "password",
        "default": null,
        "title": "密码"
    },
    "education": {
        "type": "string",
        "default": "bachelor",
        "title": "学历",
        "options": [
            {
                "value": "bachelor",
                "title": "本科"
            },
            {
                "value": "master",
                "title": "研究生"
            } 
        ]
    }
}
```

`prefs.json` 文件的内容是一个对象数据结构，key 是 配置项的标识
每个配置项有以下属性：
 - `title: string`: 配置项的标题，必要
 - `type: string`: 数据类型，必要
   - `boolean` 布尔类型
   - `number` 数字类型（浮点和整数都用这个）
   - `string` 字符串类型
   - `password` 密码类型 **密码类型是明文存储**
 - `default: any`: 配置项的默认值，必要，数据类型取决于 `type` 的值
 - `options: []`: 可供选择的条目，可选，如果设置了，用户点击时会提供一个列表来选择，数组条目数据结构如下：
   - `value: any`: 条目的值
   - `title: string`: 条目的标题