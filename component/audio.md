# audio 组件
> 用于音频播放

audio 组件额外支持设置以下属性：
 - `url: Url`: 音频播放地址
 - `headers: object`: 设置视频网络请求时的 Http 头

```javascript
{
  // ...
  headers: {
    'User-Agent': 'Dora.js/1.0.2',
    'Cookies': '...'
  }   
  // ...
}
```
 - `hasPrevious: boolean`: 是否还有上一个节目
 - `onPrevious()`: 用户点击了“上一个”按钮的回调，应该在这个回调中更改为上一个节目信息
 - `hasNext: boolean`: 是否还有下一个节目
 - `onNext()`: 用户点击了“下一个”按钮的回调，应该在这个回调中更改为下一个节目信息