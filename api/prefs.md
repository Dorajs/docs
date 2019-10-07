# $prefs
> 读取和设置配置项

## get(key): any?
读取一个配置项的值，返回值类型取决于 `prefs.json` 中设置的数据类型

参数:
 - `key: string` 配置项的 key

## set(key, value)
设置一个配置项的值

参数：
 - `key: string` 配置项的 key
 - `value: any?` 配置项的值，类型需要和 `prefs.json` 中设置的数据类型保持一致

## all(): object
获取所有配置项的 key-value 值