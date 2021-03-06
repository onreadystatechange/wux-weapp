# Toast 提示框

一种轻量级反馈/提示，可以用来显示不会打断用户操作的内容，适合用于页面转场、数据交互的等场景中。

## 使用指南

### 在 page.json 中引入组件

```json
{
    "navigationBarTitleText": "Toast",
    "usingComponents": {
        "wux-toast": "../../dist/toast/index"
    }
}
```

### 示例

!> 该组件主要依靠 JavaScript 主动调用，所以一般只需在 wxml 中添加一个组件，并设置 id 为 `#wux-toast` 或其他，之后在 page.js 中调用 `$wuxToast(id)` 获取匹配到的第一个组件实例对象。

```html
<wux-toast id="wux-toast" />

<view class="page">
    <view class="page__hd">
        <view class="page__title">Toast</view>
        <view class="page__desc">提示框</view>
    </view>
    <view class="page__bd">
        <view class="weui-btn-area">
            <button class="weui-btn" type="default" bindtap="showToast">成功提示</button>
	        <button class="weui-btn" type="default" bindtap="showToastCancel">取消提示</button>
	        <button class="weui-btn" type="default" bindtap="showToastErr">禁止提示</button>
	        <button class="weui-btn" type="default" bindtap="showToastText">文本提示</button>
        </view>
    </view>
</view>
```

```js
import { $wuxToast } from '../../dist/index'

Page({
    data: {},
    onLoad() {},
    showToast() {
        $wuxToast().show({
            type: 'success',
            duration: 1500,
            color: '#fff',
            text: '已完成',
            success: () => console.log('已完成')
        })
    },
    showToastCancel() {
        $wuxToast().show({
            type: 'cancel',
            duration: 1500,
            color: '#fff',
            text: '取消操作',
            success: () => console.log('取消操作')
        })
    },
    showToastErr() {
        $wuxToast().show({
            type: 'forbidden',
            duration: 1500,
            color: '#fff',
            text: '禁止操作',
            success: () => console.log('禁止操作')
        })
    },
    showToastText() {
        $wuxToast().show({
            type: 'text',
            duration: 1500,
            color: '#fff',
            text: '文本提示',
            success: () => console.log('文本提示')
        })
    },
})
```

## 视频

[Toast](./_media/toast.mp4 ':include :type=iframe width=375px height=667px')

## API

| 参数 | 类型 | 描述 | 默认值 |
| --- | --- | --- | --- |
| options | <code>object</code> | 配置项 | - |
| options.type | <code>string</code> | 提示类型，可选值为 success、cancel、forbidden、text | success |
| options.duration | <code>number</code> | 提示延迟时间 | 1500 |
| options.color | <code>string</code> | 图标颜色 | #fff |
| options.text | <code>string</code> | 提示文本 | 已完成 |
| options.success | <code>function</code> | 关闭后的回调函数 | - |