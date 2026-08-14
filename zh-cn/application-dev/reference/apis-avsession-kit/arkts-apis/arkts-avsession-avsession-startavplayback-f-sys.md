# startAVPlayback（系统接口）

## startAVPlayback

```TypeScript
function startAVPlayback(bundleName: string, assetId: string): Promise<void>
```

启动媒体播放应用程序。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function startAVPlayback(bundleName: string, assetId: string): Promise<void>--><!--Device-avSession-function startAVPlayback(bundleName: string, assetId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定应用包名。 |
| assetId | string | 是 | 指定媒体ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当播放成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |

## 示例

```TypeScript
import { audio } from '@kit.AudioKit';

avSession.startAVPlayback("com.example.myapplication", "121278").then(() => {
  console.info('Succeeded in starting AV playback.');
});
```


## startAVPlayback

```TypeScript
function startAVPlayback(bundleName: string, assetId: string, info: CommandInfo): Promise<void>
```

携带启动参数的冷启动应用播放接口

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function startAVPlayback(bundleName: string, assetId: string, info: CommandInfo): Promise<void>--><!--Device-avSession-function startAVPlayback(bundleName: string, assetId: string, info: CommandInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Specifies the bundleName which to be started. |
| assetId | string | 是 | Specifies the assetId to be started. |
| info | [CommandInfo](arkts-avsession-avsession-commandinfo-i.md) | 是 | Specifies the specified command information. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

