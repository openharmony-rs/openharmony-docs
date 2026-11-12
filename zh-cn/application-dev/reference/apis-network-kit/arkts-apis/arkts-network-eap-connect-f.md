# connect

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## connect

```TypeScript
function connect(action: EthEapConnectAction): Promise<void>
```

手动触发或断开以太网的802.1X EAP认证。

当**action**为**Action_CONNECT***时，将使用保存的配置(自动身份验证触发器的手动对应项；如果没有配置，则失败已存储)。如果鉴权被企业应用占用，则该接口不会中断它；结果通过stateChange回调传递。当**action**为**Action_DISCONNECT**时，自动身份验证将停止，并且底层802.1X认证已注销。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function connect(action: EthEapConnectAction): Promise<void>--><!--Device-eap-function connect(action: EthEapConnectAction): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [EthEapConnectAction](arkts-network-eap-etheapconnectaction-e.md) | 是 | 手动连接动作：重新触发认证（**Action_CONNECT**）或断开连接(**ACTION_DISCONNECT**)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
