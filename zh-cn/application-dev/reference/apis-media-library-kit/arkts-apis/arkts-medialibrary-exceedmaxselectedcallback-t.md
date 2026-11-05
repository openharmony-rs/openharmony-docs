# ExceedMaxSelectedCallback

```TypeScript
export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void
```

选择达到最大选择数量之后再次点击勾选时的回调事件。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void--><!--Device-unnamed-export type ExceedMaxSelectedCallback = (exceedMaxCountType: MaxCountType) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exceedMaxCountType | [MaxCountType](arkts-medialibrary-file-photopickercomponent-maxcounttype-e.md) | 是 | 达到最大选择数量的类型。类型包含图片最大选择数量、视频最大选择数量以及总的最大选择数量。 |
