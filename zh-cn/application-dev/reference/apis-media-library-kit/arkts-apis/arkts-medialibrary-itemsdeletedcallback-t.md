# ItemsDeletedCallback

```TypeScript
export type ItemsDeletedCallback = (baseItemInfos: Array<BaseItemInfo>) => void
```

已勾选的图片被删除时产生的回调事件。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type ItemsDeletedCallback = (baseItemInfos: Array<BaseItemInfo>) => void--><!--Device-unnamed-export type ItemsDeletedCallback = (baseItemInfos: Array<BaseItemInfo>) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| baseItemInfos | Array&lt;[BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md)&gt; | 是 | 照片的基本信息。 |
