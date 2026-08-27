# AudioSpatialDeviceState（系统接口）

空间化设备状态。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## address

```TypeScript
address: string
```

空间化设备地址。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## isHeadTrackingSupported

```TypeScript
isHeadTrackingSupported: boolean
```

空间化设备是否支持头动跟踪。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isHeadTrackingSupported: boolean = audioSpatializationManager.isHeadTrackingSupported();
  console.info(`AudioSpatializationManager isHeadTrackingSupported: ${isHeadTrackingSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## isSpatializationSupported

```TypeScript
isSpatializationSupported: boolean
```

空间化设备是否支持空间音频渲染。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let isSpatializationSupported: boolean = audioSpatializationManager.isSpatializationSupported();
  console.info(`AudioSpatializationManager isSpatializationSupported: ${isSpatializationSupported}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## spatialDeviceType

```TypeScript
spatialDeviceType: AudioSpatialDeviceType
```

空间化设备类型。

**类型：** [AudioSpatialDeviceType](arkts-audio-audio-audiospatialdevicetype-e-sys.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

let spatialDeviceState: audio.AudioSpatialDeviceState = {
  address: "123",
  isSpatializationSupported: true,
  isHeadTrackingSupported: true,
  spatialDeviceType: audio.AudioSpatialDeviceType.SPATIAL_DEVICE_TYPE_IN_EAR_HEADPHONE
};
```
