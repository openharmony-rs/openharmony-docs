# AudioCapturer

提供音频采集的相关接口。

在使用AudioCapturer的接口之前，需先通过[createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md#createaudiocapturer-1)获取AudioCapturer实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 8开始支持。

**起始版本：** 8

<!--Device-audio-interface AudioCapturer--><!--Device-audio-interface AudioCapturer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## offReadMicInData

```TypeScript
offReadMicInData(callback?: Callback<AudioCapturerMicInData>): void
```

取消订阅micIn音频数据回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-offReadMicInData(callback?: Callback<AudioCapturerMicInData>): void--><!--Device-AudioCapturer-offReadMicInData(callback?: Callback<AudioCapturerMicInData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioCapturerMicInData> | 否 | 用于读取缓冲的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted at running state. |

## onReadMicInData

```TypeScript
onReadMicInData(callback: Callback<AudioCapturerMicInData>): void
```

订阅micIn音频数据回调。此回调的优先级高于“readData”回调。如果此回调和'readData'回调都被订阅，则仅此回调将被调用。有关更多详细信息，请参见{@link #onReadData}。当有音频缓冲可用于读取更多数据时，触发该事件。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturer-onReadMicInData(callback: Callback<AudioCapturerMicInData>): void--><!--Device-AudioCapturer-onReadMicInData(callback: Callback<AudioCapturerMicInData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AudioCapturerMicInData> | 是 | 读取缓冲的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permitted at running state. |

## setInputDeviceToAccessory

```TypeScript
setInputDeviceToAccessory(): void
```

Sets default input device of this Capturer to DEVICE_TYPE_ACCESSORY.Other capturers' devices will not be affected by this method.This method can only be used before the capture stream starts. Besides,if audio accessory is not connected, this method will report fail. After calling this function, the input device of this capturer will not be affected by other interfaces.

**起始版本：** 19

<!--Device-AudioCapturer-setInputDeviceToAccessory(): void--><!--Device-AudioCapturer-setInputDeviceToAccessory(): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800103](../errorcode-audio.md#6800103-状态不支持) | Operation not permit at current state. |

