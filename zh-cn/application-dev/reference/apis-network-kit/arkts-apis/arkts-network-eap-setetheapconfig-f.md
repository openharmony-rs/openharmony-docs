# setEthEapConfig

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## setEthEapConfig

```TypeScript
function setEthEapConfig(config: EthEapConfig): void
```

设置以太网的802.1X EAP配置。配置是持久化的，并且是加密的。

任何字段更改都会触发一个自动身份验证周期，除非该功能被禁用或认证是由企业应用占用的(那么config只有企业应用保持控制。身份验证结果通过stateChange回调，而不是通过此API的返回。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function setEthEapConfig(config: EthEapConfig): void--><!--Device-eap-function setEthEapConfig(config: EthEapConfig): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [EthEapConfig](arkts-network-eap-etheapconfig-i.md) | 是 | 要设置的802.1X EAP配置。敏感字段(密码、certPassword、作为空字符串/空数组传递的certEntry表示“保留原始值”。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
