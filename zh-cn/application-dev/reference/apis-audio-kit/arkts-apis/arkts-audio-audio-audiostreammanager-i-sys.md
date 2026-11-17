# AudioStreamManager（系统接口）

```TypeScript
interface AudioStreamManager
```

AudioStreamManager是音频系统中的音频流管理模块。本模块提供音频流生命周期管理能力，包括音频渲染器和采集器的信息查询、状态监听、音效模式管理等。当开发者需要实时掌握音频流状态变化以优化音频应用用户体验时，使用本模块接口完成相关操作。在使用AudioStreamManager的接口之前，需先通过[getStreamManager](arkts-audio-audio-audiomanager-i.md#getstreammanager)获取AudioStreamManager实例。

> **说明：** 

> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

<!--Device-audio-interface AudioStreamManager--><!--Device-audio-interface AudioStreamManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getHighestPipeStreamInfo

```TypeScript
getHighestPipeStreamInfo(deviceDescriptor: AudioDeviceDescriptor, uid?: number): Promise<AudioStreamInfo | null>
```

获取路由到指定设备的播放流实际所选通路中最高规格的流信息。

> **说明：** 
> 返回的格式是系统路由后实际所选通路的格式，可能与创建流时请求的格式不同。不指定uid时查询所有应用的流。没有播放流路由到指定设备时返回null，包括应用没有创建AudioRenderer或应用创建的AudioRenderer输出设备不是传入的设备。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioStreamManager-getHighestPipeStreamInfo(deviceDescriptor: AudioDeviceDescriptor, uid?: int): Promise<AudioStreamInfo | null>--><!--Device-AudioStreamManager-getHighestPipeStreamInfo(deviceDescriptor: AudioDeviceDescriptor, uid?: int): Promise<AudioStreamInfo | null>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 是 | 音频设备描述符。 |
| uid | number | 否 | 表示要指定查询的应用ID。该参数为可选参数。<br>取值限定为整数。默认值：不指定是查询所有应用的流信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) &#124; null&gt; | Promise用于返回流信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. Eusure that the specified AudioDeviceDescriptor is valid and the device exists. Ensure that the specified uid is valid. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | System error. An unexpected error occurred in audio system. |
