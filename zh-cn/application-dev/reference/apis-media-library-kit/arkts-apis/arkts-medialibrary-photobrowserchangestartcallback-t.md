# PhotoBrowserChangeStartCallback

```TypeScript
export type PhotoBrowserChangeStartCallback = (targetPhotoInfo: BaseItemInfo) => void
```

宫格视图进入到大图视图、大图浏览切换时产生的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type PhotoBrowserChangeStartCallback = (targetPhotoInfo: BaseItemInfo) => void--><!--Device-unnamed-export type PhotoBrowserChangeStartCallback = (targetPhotoInfo: BaseItemInfo) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetPhotoInfo | [BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md) | 是 | 照片的基本信息。<br>**注意：** <br>返回信息只包含[BaseItemInfo](arkts-medialibrary-file-photopickercomponent-baseiteminfo-c.md)中的uri、photoSubType、mimeType和movingPhotoBadgeState。 |
