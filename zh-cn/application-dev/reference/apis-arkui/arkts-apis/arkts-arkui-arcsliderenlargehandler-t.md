# ArcSliderEnlargeHandler

```TypeScript
declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void
```

弧形Slider放大或缩小时，告知应用。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void--><!--Device-unnamed-declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnlarged | boolean | 是 | ArcSlider当前是否放大。<br/>isEnlarged为false时，ArcSlider组件处于缩小状态。<br/>isEnlarged为true时， ArcSlider组件处于放大状态。  |

