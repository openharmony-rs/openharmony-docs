# PickerProfile

相机选择器的配置信息。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## cameraPosition

```TypeScript
cameraPosition: camera.CameraPosition
```

相机的位置。

**类型：** camera.CameraPosition

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## saveUri

```TypeScript
saveUri?: string
```

保存配置信息的uri，默认值请参考[文件uri](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。当前saveUri参数为可选参数，若未配置该参数，则拍摄的照片和视频 会默认存入媒体库中；若不想将照片和视频存入媒体库中，请自行配置应用沙箱内的文件资源路径，如自行传入资源路径时请确保该文件存在且具备写入权限，否则会保存失败。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## videoDuration

```TypeScript
videoDuration?: number
```

录制的最大时长（单位：秒）。默认为0，不设置最大录制时长。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
