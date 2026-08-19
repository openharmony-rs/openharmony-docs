# CameraOutputCapability

相机输出能力项。

**起始版本：** 23

<!--Device-camera-interface CameraOutputCapability--><!--Device-camera-interface CameraOutputCapability-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## photoProfiles

```TypeScript
readonly photoProfiles: Array<Profile>
```

支持的拍照配置信息集合。

**类型：** Array&lt;[Profile](arkts-camera-camera-profile-i.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOutputCapability-readonly photoProfiles: Array<Profile>--><!--Device-CameraOutputCapability-readonly photoProfiles: Array<Profile>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## previewProfiles

```TypeScript
readonly previewProfiles: Array<Profile>
```

支持的预览配置信息集合。

**类型：** Array&lt;[Profile](arkts-camera-camera-profile-i.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOutputCapability-readonly previewProfiles: Array<Profile>--><!--Device-CameraOutputCapability-readonly previewProfiles: Array<Profile>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## supportedMetadataObjectTypes

```TypeScript
readonly supportedMetadataObjectTypes: Array<MetadataObjectType>
```

支持的metadata流类型信息集合。

**类型：** Array&lt;[MetadataObjectType](arkts-camera-camera-metadataobjecttype-e.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOutputCapability-readonly supportedMetadataObjectTypes: Array<MetadataObjectType>--><!--Device-CameraOutputCapability-readonly supportedMetadataObjectTypes: Array<MetadataObjectType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## videoProfiles

```TypeScript
readonly videoProfiles: Array<VideoProfile>
```

支持的录像配置信息集合。

**类型：** Array&lt;[VideoProfile](arkts-camera-camera-videoprofile-i.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOutputCapability-readonly videoProfiles: Array<VideoProfile>--><!--Device-CameraOutputCapability-readonly videoProfiles: Array<VideoProfile>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

