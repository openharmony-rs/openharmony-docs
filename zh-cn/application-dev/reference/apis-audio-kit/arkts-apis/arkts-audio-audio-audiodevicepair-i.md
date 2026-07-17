# AudioDevicePair

描述返听使用的音频设备对，包含输入设备和输出设备。

**起始版本：** 26.0.0

<!--Device-audio-interface AudioDevicePair--><!--Device-audio-interface AudioDevicePair-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## inputDevice

```TypeScript
inputDevice: AudioDeviceDescriptor
```

输入音频设备描述。

**类型：** AudioDeviceDescriptor

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDevicePair-inputDevice: AudioDeviceDescriptor--><!--Device-AudioDevicePair-inputDevice: AudioDeviceDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## outputDevice

```TypeScript
outputDevice: AudioDeviceDescriptor
```

输出音频设备描述。

**类型：** AudioDeviceDescriptor

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioDevicePair-outputDevice: AudioDeviceDescriptor--><!--Device-AudioDevicePair-outputDevice: AudioDeviceDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

