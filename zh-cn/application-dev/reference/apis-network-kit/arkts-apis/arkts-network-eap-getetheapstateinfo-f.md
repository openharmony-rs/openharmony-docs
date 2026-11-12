# getEthEapStateInfo

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## getEthEapStateInfo

```TypeScript
function getEthEapStateInfo(): EthEapStateInfo
```

查询当前802.1X EAP认证状态信息。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function getEthEapStateInfo(): EthEapStateInfo--><!--Device-eap-function getEthEapStateInfo(): EthEapStateInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md) | 当前身份验证状态、重试次数和补充消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
