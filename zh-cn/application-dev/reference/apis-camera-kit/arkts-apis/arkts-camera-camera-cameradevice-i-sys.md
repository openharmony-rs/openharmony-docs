# CameraDevice

相机设备信息。

**起始版本：** 23

<!--Device-camera-interface CameraDevice--><!--Device-camera-interface CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## hostDeviceName

```TypeScript
readonly hostDeviceName: string
```

远端设备名称。若当前无远端设备，返回为空。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly hostDeviceName: string--><!--Device-CameraDevice-readonly hostDeviceName: string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## hostDeviceType

```TypeScript
readonly hostDeviceType: HostDeviceType
```

远端设备类型。

**类型：** [HostDeviceType](arkts-camera-camera-hostdevicetype-e-sys.md)

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly hostDeviceType: HostDeviceType--><!--Device-CameraDevice-readonly hostDeviceType: HostDeviceType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## isRetractable

```TypeScript
readonly isRetractable?: boolean
```

Camera device retractable attribute

**类型：** boolean

**起始版本：** 23

<!--Device-CameraDevice-readonly isRetractable?: boolean--><!--Device-CameraDevice-readonly isRetractable?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## lensEquivalentFocalLength

```TypeScript
readonly lensEquivalentFocalLength?: Array<int>
```

相机镜头等效焦距。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly lensEquivalentFocalLength?: Array<int>--><!--Device-CameraDevice-readonly lensEquivalentFocalLength?: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

