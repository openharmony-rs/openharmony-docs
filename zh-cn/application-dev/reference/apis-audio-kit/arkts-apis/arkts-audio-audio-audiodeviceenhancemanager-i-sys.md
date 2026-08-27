# AudioDeviceEnhanceManager

音频设备增强管理功能，用于应用级音频设备选择及流维度音频设备选择。 在使用AudioDeviceEnhanceManager的接口之前，需要先通过getDeviceEnhanceManager获取AudioDeviceEnhanceManager实例。

> **说明：**
> 
> 应用在使用前应先调用isEnhancedRoutingSupported，确认系统是否支持音频设备增强管理功能。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getSoundCardInfo

```TypeScript
getSoundCardInfo(): Promise<SoundCardInfo>
```

获取声卡信息。此方法使用 Promise 返回查询结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.DeviceEnhance

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SoundCardInfo](arkts-audio-audio-soundcardinfo-i-sys.md)&gt; | Promise 过去用于返回声卡信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let deviceEnhanceManager = audioManager.getDeviceEnhanceManager();

deviceEnhanceManager.getSoundCardInfo().then((soundCardInfo: audio.SoundCardInfo) => {
  console.info(`Successfully obtained sound card info: ${JSON.stringify(soundCardInfo, null, 2)}`);
})
.catch((err: BusinessError) => {
  console.error(`Failed to get sound card info. Code: ${err.code}, Message: ${err.message}`);
});
```
