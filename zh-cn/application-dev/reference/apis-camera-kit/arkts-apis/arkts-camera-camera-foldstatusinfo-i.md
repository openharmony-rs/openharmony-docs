# FoldStatusInfo

相机管理器回调返回的接口实例，表示折叠机折叠状态信息。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface FoldStatusInfo--><!--Device-camera-interface FoldStatusInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## foldStatus

```TypeScript
readonly foldStatus: FoldStatus
```

折叠屏折叠状态。

**类型：** FoldStatus

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatusInfo-readonly foldStatus: FoldStatus--><!--Device-FoldStatusInfo-readonly foldStatus: FoldStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## supportedCameras

```TypeScript
readonly supportedCameras: Array<CameraDevice>
```

当前折叠状态所支持的相机信息列表。

**类型：** Array&lt;CameraDevice&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FoldStatusInfo-readonly supportedCameras: Array<CameraDevice>--><!--Device-FoldStatusInfo-readonly supportedCameras: Array<CameraDevice>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

