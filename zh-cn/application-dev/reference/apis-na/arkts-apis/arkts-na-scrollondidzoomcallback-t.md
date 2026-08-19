# ScrollOnDidZoomCallback

```TypeScript
export type ScrollOnDidZoomCallback = (scale: double) => void
```

Scroll每帧缩放完成时触发的回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ScrollOnDidZoomCallback = (scale: double) => void--><!--Device-unnamed-export type ScrollOnDidZoomCallback = (scale: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | double | 是 | 当前缩放倍数。 |

