# ArcSliderEnlargeHandler

```TypeScript
export declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void
```

弧形Slider放大或缩小时，告知应用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void--><!--Device-unnamed-export declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnlarged | boolean | 是 | ArcSlider当前是否放大。<br/>isEnlarged为false时，ArcSlider组件处于缩小状态。<br/>isEnlarged为true时， ArcSlider组件处于放大状态。 |

