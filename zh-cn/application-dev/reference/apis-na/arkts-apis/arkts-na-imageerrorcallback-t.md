# ImageErrorCallback

```TypeScript
export type ImageErrorCallback = (error: ImageError) => void
```

图片加载异常时触发此回调。 当组件的参数类型为 AnimatedDrawableDescriptor时该事件不触发。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ImageErrorCallback = (error: ImageError) => void--><!--Device-unnamed-export type ImageErrorCallback = (error: ImageError) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [ImageError](arkts-na-image-imageerror-i.md) | 是 |  |

