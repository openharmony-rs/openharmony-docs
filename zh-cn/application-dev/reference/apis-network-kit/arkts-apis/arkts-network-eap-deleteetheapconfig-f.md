# deleteEthEapConfig

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## deleteEthEapConfig

```TypeScript
function deleteEthEapConfig(): Promise<void>
```

删除保留的802.1X EAP配置并停止任何正在进行的自动身份验证。幂等性：即使没有存储任何配置，也能成功解析。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_EAP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-eap-function deleteEthEapConfig(): Promise<void>--><!--Device-eap-function deleteEthEapConfig(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 当配置被删除时解析的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
