# PinchGridSwitchedCallback

```TypeScript
export type PinchGridSwitchedCallback = (gridLevel: photoAccessHelper.GridLevel) => void
```

用户在宫格组件内捏合时产生的回调事件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type PinchGridSwitchedCallback = (gridLevel: photoAccessHelper.GridLevel) => void--><!--Device-unnamed-export type PinchGridSwitchedCallback = (gridLevel: photoAccessHelper.GridLevel) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gridLevel | [photoAccessHelper.GridLevel](arkts-medialibrary-photoaccesshelper-gridlevel-e.md) | 是 | 宫格列数的档位。 |
