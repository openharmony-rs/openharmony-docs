# SaveMode

```TypeScript
export declare enum SaveMode
```

图片/视频保存模式。

**起始版本：** 15

<!--Device-unnamed-export declare enum SaveMode--><!--Device-unnamed-export declare enum SaveMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## OVERWRITE

```TypeScript
OVERWRITE = 1
```

覆盖原有图片/视频，覆盖后支持在图库中将保存内容回退，还原成原始图片/视频。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

<!--Device-SaveMode-OVERWRITE = 1--><!--Device-SaveMode-OVERWRITE = 1-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SAVE_AS

```TypeScript
SAVE_AS = 0
```

另存为新的图片/视频。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

<!--Device-SaveMode-SAVE_AS = 0--><!--Device-SaveMode-SAVE_AS = 0-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
