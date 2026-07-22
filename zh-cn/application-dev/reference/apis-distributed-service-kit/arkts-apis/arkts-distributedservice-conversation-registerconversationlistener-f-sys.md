# registerConversationListener（系统接口）

## 导入模块

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## registerConversationListener

```TypeScript
function registerConversationListener(
    bundleName: string,
    abilityName: string,
    dataCallback: DataCallback,
  ): void
```

注册会话监听，接收来自同一账号下可信设备的数据。当远端设备通过[postConversationData](arkts-distributedservice-conversation-postconversationdata-f-sys.md#postconversationdata)发送数据到达本地设备后，数据分发至与Bundle名和Ability名匹配的已注册回调函数。同一Bundle名和Ability名只能注册一个监听器，重复注册将覆盖之前已注册的监听器。

**配对调用**：需与注销监听器[unregisterConversationListener](arkts-distributedservice-conversation-unregisterconversationlistener-f-sys.md#unregisterconversationlistener)配对使用，不再需要接收消息时应调用注销监听器以释放资源，未注销会导致资源持续占用。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-conversation-function registerConversationListener(    bundleName: string,    abilityName: string,    dataCallback: DataCallback,  ): void--><!--Device-conversation-function registerConversationListener(    bundleName: string,    abilityName: string,    dataCallback: DataCallback,  ): void-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 接收数据的Bundle名，Bundle名长度范围为1-127字节，需与本应用的Bundle名一致。不满足此要求时，监听器无法正确接收数据。传入无效或空值时返回错误码401。 |
| abilityName | string | 是 | 接收数据的Ability名，Ability名长度范围为1-127字节，需与本应用中的Ability名一致。不满足此要求时，监听器无法正确接收数据。传入无效或空值时返回错误码401。 |
| dataCallback | [DataCallback](arkts-distributedservice-conversation-datacallback-t-sys.md) | 是 | 收到数据时的回调函数，用于接收跨设备数据。传入无效值时返回错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid parameter. The bundleName, abilityName or dataCallback is invalid or empty. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2000001](../../apis-distributedservice-kit/errorcode-conversation.md#2000001-内部) | Internal error. |

