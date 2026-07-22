# unregisterConversationListener（系统接口）

## 导入模块

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## unregisterConversationListener

```TypeScript
function unregisterConversationListener(bundleName: string, abilityName: string): void
```

注销指定Bundle名和Ability名的会话监听。需与注册监听器[registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md#registerconversationlistener)配对使用，用于注销已注册的会话监听器。在不再需要接收消息时应调用注销监听器以释放资源，未注销会导致资源持续占用。同一Bundle名和Ability名只能注册一个监听器，重复注册会覆盖之前的监听器，注销后将移除当前生效的监听器。调用此接口后，应用将不再接收对应Bundle名和Ability名的会话数据。如果之前未注册过指定Bundle名和Ability名的监听器，此接口同样返回成功。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-conversation-function unregisterConversationListener(bundleName: string, abilityName: string): void--><!--Device-conversation-function unregisterConversationListener(bundleName: string, abilityName: string): void-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要取消监听的Bundle名，Bundle名长度范围为1-127字节，需与注册监听时使用的Bundle名一致。传入无效或空值时返回错误码401。 |
| abilityName | string | 是 | 要取消监听的Ability名，Ability名长度范围为1-127字节，需与注册监听时使用的Ability名一致。传入无效或空值时返回错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid parameter. The bundleName or abilityName is invalid or empty. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2000001](../../apis-distributedservice-kit/errorcode-conversation.md#2000001-内部) | Internal error. |

