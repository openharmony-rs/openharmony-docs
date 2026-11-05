# ErrorCallback

```TypeScript
export type ErrorCallback = (pickerError: PickerError) => void
```

图片选择器组件产生错误时的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type ErrorCallback = (pickerError: PickerError) => void--><!--Device-unnamed-export type ErrorCallback = (pickerError: PickerError) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerError | [PickerError](arkts-medialibrary-file-photopickercomponent-pickererror-c.md) | 是 | 产生的错误的基本信息。 |
