# RecentPhotoCheckInfoCallback

```TypeScript
export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void
```

最近图片是否存在查询结果以及最近图片相关信息的回调事件。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void--><!--Device-unnamed-export type RecentPhotoCheckInfoCallback = (recentPhotoExists: boolean, info: RecentPhotoInfo) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recentPhotoExists | boolean | 是 | 查询最近图片是否存在，true为存在，false为不存在。 |
| info | [RecentPhotoInfo](arkts-medialibrary-file-recentphotocomponent-recentphotoinfo-c.md) | 是 | 最近图片相关信息。 |
