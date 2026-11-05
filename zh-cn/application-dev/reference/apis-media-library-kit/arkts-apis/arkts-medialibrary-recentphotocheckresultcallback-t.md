# RecentPhotoCheckResultCallback

```TypeScript
export type RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => void
```

最近图片查询结果回调事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => void--><!--Device-unnamed-export type RecentPhotoCheckResultCallback = (recentPhotoExists: boolean) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recentPhotoExists | boolean | 是 | 查询最近图片是否存在，true为存在，false为不存在。 |
