# AudioSpatialEnabledStateForDevice（系统接口）

监听设备空间音频开关状态。

@interface AudioSpatialEnabledStateForDevice

**起始版本：** 12

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

音频设备描述。

**类型：** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## enabled

```TypeScript
enabled: boolean
```

空间化或头部追踪或自适应空间渲染启用状态。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。
