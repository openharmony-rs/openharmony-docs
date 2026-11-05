# PhotoBrowserZoomCallback

```TypeScript
export type PhotoBrowserZoomCallback = (scale: number) => void
```

图片选择器组件进入大图后，大图放大缩小时的回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type PhotoBrowserZoomCallback = (scale: double) => void--><!--Device-unnamed-export type PhotoBrowserZoomCallback = (scale: double) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number | 是 | 图片相比原图放大缩小的比例。 |
