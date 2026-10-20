# AudioLoopback

```TypeScript
interface AudioLoopback
```

提供音频返听的相关接口。在使用AudioLoopback的接口之前，需先通过[audio.createAudioLoopback](arkts-audio-audio-createaudioloopback-f.md)获取AudioLoopback实例。当启用音频返听时，系统会创建低时延渲染器与低时延采集器，实现低时延耳返功能。采集的音频直接通过内部路由返回到渲染器。对于渲染器，其音频焦点策略与[STREAM_USAGE_MUSIC](arkts-audio-audio-streamusage-e.md)相匹配。对于采集器，其音频焦点策略与[SOURCE_TYPE_MIC](arkts-audio-audio-sourcetype-e.md)相匹配。输入/输出设备由系统自动选择。如果当前输入/输出不支持低时延，则音频返听无法启用。在运行过程中，如果音频焦点被另一个音频流抢占，输入/输出设备切换到不支持低时延的设备，系统会自动禁用音频返听。

> **说明：** 

> - 本Interface首批接口从API version 20开始支持。

**起始版本：** 20

<!--Device-audio-interface AudioLoopback--><!--Device-audio-interface AudioLoopback-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAvailableStatus

```TypeScript
getAvailableStatus(): AudioLoopbackAvailableStatus
```

获取全局音频返听可用状态。此功能仅适用于播控应用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopback-getAvailableStatus(): AudioLoopbackAvailableStatus--><!--Device-AudioLoopback-getAvailableStatus(): AudioLoopbackAvailableStatus-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioLoopbackavailablestatus | 全局环回的可用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 调用方不是系统应用程序。 |

## offAvailableStatusChange

```TypeScript
offAvailableStatusChange(callback?: Callback<AudioLoopbackAvailableStatus>): void
```

取消订阅全局音频返听可用状态变化事件。取消后，系统将不再触发回调。此功能仅适用于播控应用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopback-offAvailableStatusChange(callback?: Callback<AudioLoopbackAvailableStatus>): void--><!--Device-AudioLoopback-offAvailableStatusChange(callback?: Callback<AudioLoopbackAvailableStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioLoopbackAvailableStatus](arkts-audio-audio-audioloopbackavailablestatus-i-sys.md)&gt; | 否 | 待取消的回调。<br>如果不传callback参数，则取消所有订阅的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 调用方不是系统应用程序。 |

## onAvailableStatusChange

```TypeScript
onAvailableStatusChange(callback: Callback<AudioLoopbackAvailableStatus>): void
```

订阅全局音频返听可用状态变化事件。此功能仅适用于播控应用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioLoopback-onAvailableStatusChange(callback: Callback<AudioLoopbackAvailableStatus>): void--><!--Device-AudioLoopback-onAvailableStatusChange(callback: Callback<AudioLoopbackAvailableStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioLoopbackAvailableStatus](arkts-audio-audio-audioloopbackavailablestatus-i-sys.md)&gt; | 是 | 回调函数，用于返回变化后的音频返听可用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | 调用方不是系统应用程序。 |
