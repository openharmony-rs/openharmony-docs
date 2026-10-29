# startAVPlaybackForAudioZone（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## startAVPlaybackForAudioZone

```TypeScript
function startAVPlaybackForAudioZone(userId: number, bundleName: string, assetId: string,
    info?: CommandInfo, extraInfo?: ExtraInfo): Promise<void>
```

使用特定音频区域的命令信息启动媒体播放应用程序。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avSession-function startAVPlaybackForAudioZone(userId: int, bundleName: string, assetId: string,    info?: CommandInfo, extraInfo?: ExtraInfo): Promise<void>--><!--Device-avSession-function startAVPlaybackForAudioZone(userId: int, bundleName: string, assetId: string,    info?: CommandInfo, extraInfo?: ExtraInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 属于音频区域的用户ID。<br>取值限定为整数。 |
| bundleName | string | 是 | 指定要启动的bundleName。 |
| assetId | string | 是 | 指定要启动的assetId。 |
| info | [CommandInfo](arkts-avsession-avsession-commandinfo-i.md) | 否 | 指定命令信息。 |
| extraInfo | [ExtraInfo](arkts-avsession-avsession-extrainfo-t.md) | 否 | 冷启动的扩展信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [6700101](../errorcode-avsession.md#6700101-会话服务未运行) | Session service is not running. |
