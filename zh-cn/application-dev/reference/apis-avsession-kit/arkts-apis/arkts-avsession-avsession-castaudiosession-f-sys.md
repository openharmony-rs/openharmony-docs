# castAudioSession（系统接口）

## castAudioSession

```TypeScript
function castAudioSession(session: SessionToken, audioDevices: Array<audio.AudioDeviceDescriptor>, callback: AsyncCallback<void>): void
```

Cast Audio to the remote devices or cast back local device

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function castAudioSession(session: SessionToken, audioDevices: Array<audio.AudioDeviceDescriptor>, callback: AsyncCallback<void>): void--><!--Device-avSession-function castAudioSession(session: SessionToken, audioDevices: Array<audio.AudioDeviceDescriptor>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 是 | Specifies the sessionId which to send to remote. |
| audioDevices | Array&lt;audio.AudioDeviceDescriptor&gt; | 是 | Specifies the audio devices to cast. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | The asyncCallback triggered when the command is executed successfully |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600104](../errorcode-avsession.md#6600104-远端会话连接失败) | The remote session connection failed. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';
let audioManager = audio.getAudioManager();
let audioRoutingManager = audioManager.getRoutingManager();
let audioDevices: audio.AudioDeviceDescriptors | undefined = undefined;
audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((data) => {
  audioDevices = data;
  console.info('Promise returned to indicate that the device list is obtained.');
}).catch(async(err) => {
});

let sessionToken: avSession.SessionToken = {
  sessionId: 'token'
};

if (audioDevices !== undefined) {
  avSession.castAudioSession(sessionToken, audioDevices as audio.AudioDeviceDescriptors, (err | null) => {
    console.info('CastAudio : SUCCESS ');
  });
}
```


## castAudioSession

```TypeScript
function castAudioSession(session: SessionToken, audioDevices: Array<audio.AudioDeviceDescriptor>): Promise<void>
```

Cast Audio to the remote devices or cast back local device

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function castAudioSession(session: SessionToken, audioDevices: Array<audio.AudioDeviceDescriptor>): Promise<void>--><!--Device-avSession-function castAudioSession(session: SessionToken, audioDevices: Array<audio.AudioDeviceDescriptor>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 是 | Specifies the sessionId which to send to remote. |
| audioDevices | Array&lt;audio.AudioDeviceDescriptor&gt; | 是 | Specifies the audio devices to cast. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600104](../errorcode-avsession.md#6600104-远端会话连接失败) | The remote session connection failed. |

