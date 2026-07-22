# postConversationData（系统接口）

## 导入模块

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## postConversationData

```TypeScript
function postConversationData(
    deviceId: string,
    bundleName: string,
    abilityName: string,
    msg: ArrayBuffer
): Promise<void>
```

向目标设备发送会话数据。目标设备须为同一账号下的可信设备。以目标设备的networkId或UDID进行设备寻址，数据发送至目标设备上与指定Bundle名和Ability名匹配的已注册监听应用。典型使用场景包括：跨设备协同指令发送。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-conversation-function postConversationData(    deviceId: string,    bundleName: string,    abilityName: string,    msg: ArrayBuffer): Promise<void>--><!--Device-conversation-function postConversationData(    deviceId: string,    bundleName: string,    abilityName: string,    msg: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 目标设备的networkId或UDID。可通过调用[getTrustedDevices()](arkts-distributedservice-conversation-gettrusteddevices-f-sys.md#gettrusteddevices)获取。networkId、UDID的长度都应为64字节。传入无效值时返回错误码401。 |
| bundleName | string | 是 | 数据发送目标Bundle名，Bundle名长度范围为1-127字节，需与目标设备上通过[registerConversationListener](arkts-distributedservice-conversation-registerconversationlistener-f-sys.md#registerconversationlistener)注册会话监听的应用Bundle名一致。不满足此要求时，数据将无法送达目标应用。传入无效或空值时返回错误码401。 |
| abilityName | string | 是 | 数据发送目标Ability名，Ability名长度范围为1-127字节，需与目标设备上已注册会话监听的Ability名一致。不满足此要求时，数据将无法送达目标应用。传入无效或空值时返回错误码401。 |
| msg | ArrayBuffer | 是 | 要发送的数据内容，一次调用最大支持发送10240字节。数据结构由应用层协议定义。传入空数据或无效数据时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid parameter. The deviceId, bundleName, abilityName or msg is invalid or empty. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2000001](../../apis-distributedservice-kit/errorcode-conversation.md#2000001-内部) | Internal error. |
| [2004001](../../apis-distributedservice-kit/errorcode-conversation.md#2004001-对端版本不支持) | Remote not support. |
| [2004002](../../apis-distributedservice-kit/errorcode-conversation.md#2004002-重复调用) | Duplicate calls, previous call still in progress. |
| [2004003](../../apis-distributedservice-kit/errorcode-conversation.md#2004003-发送失败) | Send data failed. |
| [2004004](../../apis-distributedservice-kit/errorcode-conversation.md#2004004-请求超时) | Wait remote ack timeout. |

