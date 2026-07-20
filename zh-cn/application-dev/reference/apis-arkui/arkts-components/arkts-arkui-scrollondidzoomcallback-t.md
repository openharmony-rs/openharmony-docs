# ScrollOnDidZoomCallback

```TypeScript
declare type ScrollOnDidZoomCallback = (scale: number) => void
```

Scroll每帧缩放完成时触发的回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ScrollOnDidZoomCallback = (scale: number) => void--><!--Device-unnamed-declare type ScrollOnDidZoomCallback = (scale: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | 当前缩放倍数。  |

