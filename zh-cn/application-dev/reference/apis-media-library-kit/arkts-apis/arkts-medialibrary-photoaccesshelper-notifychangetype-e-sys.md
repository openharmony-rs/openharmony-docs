# NotifyChangeType

枚举，媒体资产（图片/视频）或相册变更事件的通知类型。

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOTIFY_CHANGE_YUV_READY

```TypeScript
NOTIFY_CHANGE_YUV_READY = 3
```

分段式拍照场景下高质量图已准备完成。图像的清晰度、色彩准确度等质量指标可在请求图像的回调中判断： [OnDataPrepared](arkts-medialibrary-photoaccesshelper-quickimagedatahandler-i.md#ondataprepared)。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## NOTIFY_CHANGE_ADD_ANALYSIS

```TypeScript
NOTIFY_CHANGE_ADD_ANALYSIS = 4
```

智慧分析相册内媒体资产（图片/视频）已经创建。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## NOTIFY_CHANGE_REMOVE_ANALYSIS

```TypeScript
NOTIFY_CHANGE_REMOVE_ANALYSIS = 5
```

智慧分析相册内媒体资产（图片/视频）已经删除。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
