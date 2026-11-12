# getEthEapConfig

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## getEthEapConfig

```TypeScript
function getEthEapConfig(): Promise<EthEapConfig>
```

获取以太网的802.1X EAP配置。敏感字段（密码、certPassword、certEntry）总是返回空。如果尚未存储任何配置，则以**null**进行解析。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function getEthEapConfig(): Promise<EthEapConfig>--><!--Device-eap-function getEthEapConfig(): Promise<EthEapConfig>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[EthEapConfig](arkts-network-eap-etheapconfig-i.md)&gt; | Promise用于返回${EthEapConfig} |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
