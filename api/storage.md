# $storage
> key-value 的本地数据存储

## put(key, value)
存入一个数据，如果该 `key` 已经存在，会替换掉已有的值

参数：
 - `key: string`: 存入的 key，用于标识这个数据
 - `value: any`: 要存的值

## get(key): any
获取 `key` 的值

## all(): object
获取本地保存的所有数据，返回的是一个 key-value Map

## has(key): boolean
是否存在 `key` 的数据，返回一个布尔值

## remove(key)
删除 `key` 下面的数据
