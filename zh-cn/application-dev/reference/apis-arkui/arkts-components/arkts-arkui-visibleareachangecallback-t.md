# VisibleAreaChangeCallback

```TypeScript
declare type VisibleAreaChangeCallback = (isExpanding: boolean, currentRatio: number) => void
```

组件可见区域变化事件的回调类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isExpanding | boolean | 是 | 视组件的可见面积与自身面积的比值与上一次回调相比的情况而定，比值变大为true，比值变小为false。 |
| currentRatio | number | 是 | 触发回调时，组件可见面积与自身面积的比值。 |

