# offStateChange

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## offStateChange

```TypeScript
function offStateChange(callback?: Callback<EthEapStateInfo>): void
```

取消订阅802.1X EAP身份验证状态更改。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function offStateChange(callback?: Callback<EthEapStateInfo>): void--><!--Device-eap-function offStateChange(callback?: Callback<EthEapStateInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md)&gt; | 否 | 移除的回调。如果省略，则删除所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
