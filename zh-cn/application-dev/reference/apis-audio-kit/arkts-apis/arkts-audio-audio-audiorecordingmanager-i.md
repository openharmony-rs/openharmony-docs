# AudioRecordingManager

录音策略管理，提供协同录音和录音控制能力。 在使用AudioRecordingManager的接口之前，需先通过 getRecordingManager获取AudioRecordingManager实例 。

> **说明：**
> 
> - 本模块首批接口从API版本26.0.0开始支持。
> 
> - 本模块接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## enableSystemRecordController

```TypeScript
enableSystemRecordController(show: boolean, config: SystemRecordControllerConfig): Promise<void>
```

启用或禁用系统录音控制面板。使用Promise异步回调。

> **说明：**
> 
> - 应用可以在开始录音之前调用此接口在控制中心拉起录音控制面板，让用户完成录音设备或音频效果参数的选择，然后再启动录音服务。
> 
> - 若录音过程中调用该接口，在拉起的录音控制面板中切换录音设备或音频效果参数，会导致录制的音频效果不一致。
> 
> - 应用必须在前台才能启用该面板，如果应用在后台，启用操作不会生效。禁用面板不受应用前台或后台状态限制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 启用或禁用系统录音控制面板。true表示启用，false表示禁用。 |
| config | SystemRecordControllerConfig | 是 | 系统录音控制面板的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-系统处理异常) | Audio service error occurs like service died. |
