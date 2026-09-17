# AudioPersonalizedSpatialEnabledChangeForAnyDevice（系统接口）

此接口用于通知监听器任何设备个性化空间化启用状态的变化。

**起始版本：** 26.0.0

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

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。

## enabled

```TypeScript
enabled: boolean
```

个性化空间化已启用状态。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Spatialization

**系统接口：** 此接口为系统接口。
