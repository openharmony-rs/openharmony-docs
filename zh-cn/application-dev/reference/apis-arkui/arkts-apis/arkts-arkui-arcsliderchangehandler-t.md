# ArcSliderChangeHandler

```TypeScript
declare type ArcSliderChangeHandler = (progress: number) => void
```

弧形Slider的进度值发生变化时触发回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ArcSliderChangeHandler = (progress: number) => void--><!--Device-unnamed-declare type ArcSliderChangeHandler = (progress: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | number | 是 | Slider当前的进度值。 |

