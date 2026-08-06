# OnTabsContentWillChangeCallback

```TypeScript
export type OnTabsContentWillChangeCallback = (currentIndex: int, comingIndex: int) => boolean
```

自定义Tabs页面切换拦截事件能力，新页面即将显示时触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnTabsContentWillChangeCallback = (currentIndex: int, comingIndex: int) => boolean--><!--Device-unnamed-export type OnTabsContentWillChangeCallback = (currentIndex: int, comingIndex: int) => boolean-End-->

**系统能力：** 
- SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentIndex | int | 是 | 当前显示页面的index索引，索引从0开始计算。 取值范围为全体整数 取值限定为整数。  |
| comingIndex | int | 是 | 将要显示的新页面的index索引。 取值范围为全体整数 取值限定为整数。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - |

