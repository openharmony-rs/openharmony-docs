# ArcSliderEnlargeHandler

```TypeScript
declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void
```

弧形Slider放大或缩小时触发回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void--><!--Device-unnamed-declare type ArcSliderEnlargeHandler = (isEnlarged: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnlarged | boolean | 是 | ArcSlider当前是否放大。\_\_\_HTML\_TAG\_USD\_0\_\_\_isEnlarged为false时，ArcSlider组件处于缩小状态。\_\_\_HTML\_TAG\_USD\_1\_\_\_isEnlarged为true时， ArcSlider组件处于放大状态。  |

