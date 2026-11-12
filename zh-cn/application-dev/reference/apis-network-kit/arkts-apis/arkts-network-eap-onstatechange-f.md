# onStateChange

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## onStateChange

```TypeScript
function onStateChange(callback: Callback<EthEapStateInfo>): void
```

订阅802.1X EAP认证状态变化。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function onStateChange(callback: Callback<EthEapStateInfo>): void--><!--Device-eap-function onStateChange(callback: Callback<EthEapStateInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md)&gt; | 是 | 鉴权状态改变时调用的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
