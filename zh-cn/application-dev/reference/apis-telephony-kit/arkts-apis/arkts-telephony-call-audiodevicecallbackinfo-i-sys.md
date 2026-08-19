# AudioDeviceCallbackInfo（系统接口）

音频设备信息。

**起始版本：** 23

<!--Device-call-export interface AudioDeviceCallbackInfo--><!--Device-call-export interface AudioDeviceCallbackInfo-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## audioDeviceList

```TypeScript
audioDeviceList: Array<AudioDevice>
```

音频设备列表。

**类型：** Array&lt;[AudioDevice](arkts-telephony-call-audiodevice-i-sys.md)&gt;

**起始版本：** 23

<!--Device-AudioDeviceCallbackInfo-audioDeviceList: Array<AudioDevice>--><!--Device-AudioDeviceCallbackInfo-audioDeviceList: Array<AudioDevice>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## currentAudioDevice

```TypeScript
currentAudioDevice: AudioDevice
```

当前音频设备。

**类型：** [AudioDevice](arkts-telephony-call-audiodevice-i-sys.md)

**起始版本：** 23

<!--Device-AudioDeviceCallbackInfo-currentAudioDevice: AudioDevice--><!--Device-AudioDeviceCallbackInfo-currentAudioDevice: AudioDevice-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isMicDisabled

```TypeScript
isMicDisabled?: boolean
```

是否禁用麦克风。 - true：禁用麦克风 - false：启用麦克风

**类型：** boolean

**起始版本：** 24

<!--Device-AudioDeviceCallbackInfo-isMicDisabled?: boolean--><!--Device-AudioDeviceCallbackInfo-isMicDisabled?: boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## isMuted

```TypeScript
isMuted: boolean
```

是否静音。

**类型：** boolean

**起始版本：** 23

<!--Device-AudioDeviceCallbackInfo-isMuted: boolean--><!--Device-AudioDeviceCallbackInfo-isMuted: boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

