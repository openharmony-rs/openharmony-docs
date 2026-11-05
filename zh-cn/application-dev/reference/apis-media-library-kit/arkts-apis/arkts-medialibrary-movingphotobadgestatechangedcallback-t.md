# MovingPhotoBadgeStateChangedCallback

```TypeScript
export type MovingPhotoBadgeStateChangedCallback = 
  (uri: string, state: photoAccessHelper.MovingPhotoBadgeStateType) => void
```

用户在Picker组件中打开/关闭动态效果时的回调事件。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type MovingPhotoBadgeStateChangedCallback =   (uri: string, state: photoAccessHelper.MovingPhotoBadgeStateType) => void--><!--Device-unnamed-export type MovingPhotoBadgeStateChangedCallback =   (uri: string, state: photoAccessHelper.MovingPhotoBadgeStateType) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 动态照片uri。 |
| state | [photoAccessHelper.MovingPhotoBadgeStateType](arkts-medialibrary-photoaccesshelper-movingphotobadgestatetype-e.md) | 是 | 动态照片状态。 |
