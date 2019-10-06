# video 组件
> 用于视频播放

除了基础的成员外，video 组件的实例还有如下成员：
 - `url` 视频播放地址
 - `selectors[]` 资源选择器，如果视频有不同的线路或者不同的清晰度，可以通过 `selectors` 来进行设置

## url 属性
目前 Dora 支持以下视频类型：  
// TODO

## selectors 属性

selectors 接受一个数组，数组元素的数据结构如下：

```javascript
{
    select: 1, // number, 选中的 option 数组下标，默认为 0
    onSelect: 'onSelectQuaility' // string, 当用户选中后，会回调组件的这个方法，会把选中的 option 作为参数传入
    options: [{ // [], 可供选择的项目
        title: '高清', // 选项显示的标题
        value: any // option 的值，可以是任何类型
    },
    ....
    ]
}
```

例子: 
```javascript
module.exports = {
    async fetch() {
        let resp = await $http.get('...')
        return {
            url: resp.data.url,
            selectors: [
            {
                title: '清晰度',
                select: 0,
                onSelect: 'onSelectQuaility',
                options: [
                    {
                        title: '高清',
                        value: {
                            baseUrl: 'http://example.com'
                            qs : 1
                        }
                    },
                    {
                        title: '标准',
                        value: {
                            baseUrl: 'http://example.com'
                            qs : 2
                        }
                    }
                ]
            }]
        }
    },
    onSelectQuaility(option) {
        this.url = `${option.baseUrl}?qs=${option.qs}`
    }
}

 ```