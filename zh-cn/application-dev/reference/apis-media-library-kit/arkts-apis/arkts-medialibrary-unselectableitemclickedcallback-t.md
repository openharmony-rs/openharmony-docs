# UnselectableItemClickedCallback

```TypeScript
export type UnselectableItemClickedCallback = (unselectableItemInfo: UnselectableItemInfo) => void
```

在picker宫格或大图预览界面，当不可选中的图片被点击时产生的回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type UnselectableItemClickedCallback = (unselectableItemInfo: UnselectableItemInfo) => void--><!--Device-unnamed-export type UnselectableItemClickedCallback = (unselectableItemInfo: UnselectableItemInfo) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unselectableItemInfo | [UnselectableItemInfo](arkts-medialibrary-file-photopickercomponent-unselectableiteminfo-c.md) | 是 | 被点击的不可选中的图片详情。 |
