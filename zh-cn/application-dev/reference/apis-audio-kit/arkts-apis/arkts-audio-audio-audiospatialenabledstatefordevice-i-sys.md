# AudioSpatialEnabledStateForDevice（系统接口）

This interface is used to notify the listener of any device Spatialization or Head Tracking enable or Adaptive Spatial Rendering state change.

**起始版本：** 12

<!--Device-audio-interface AudioSpatialEnabledStateForDevice--><!--Device-audio-interface AudioSpatialEnabledStateForDevice-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## deviceDescriptor

```TypeScript
deviceDescriptor: AudioDeviceDescriptor
```

Audio device description.

**类型：** AudioDeviceDescriptor

**起始版本：** 12

<!--Device-AudioSpatialEnabledStateForDevice-deviceDescriptor: AudioDeviceDescriptor--><!--Device-AudioSpatialEnabledStateForDevice-deviceDescriptor: AudioDeviceDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## enabled

```TypeScript
enabled: boolean
```

Spatialization or Head Tracking or Adaptive Spatial Rendering enable state.

**类型：** boolean

**起始版本：** 12

<!--Device-AudioSpatialEnabledStateForDevice-enabled: boolean--><!--Device-AudioSpatialEnabledStateForDevice-enabled: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

