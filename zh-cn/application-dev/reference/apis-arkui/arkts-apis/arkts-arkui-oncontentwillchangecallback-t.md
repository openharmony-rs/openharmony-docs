# OnContentWillChangeCallback

```TypeScript
export type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean
```

页面内容即将发生变化时触发的回调函数，用于拦截页面切换，开发者可通过返回值控制是否允许切换。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean--><!--Device-unnamed-export type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentIndex | number | 是 | 当前页签索引。 |
| comingIndex | number | 是 | 即将切换的页签索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - |

