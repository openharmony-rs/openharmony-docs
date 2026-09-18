# getAllowedPrinterIPAddressesForAccount

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getAllowedPrinterIPAddressesForAccount

```TypeScript
function getAllowedPrinterIPAddressesForAccount(queryPolicy?: common.QueryPolicy): Array<string>
```

查询用户级打印机IP地址白名单

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | 否 | 查询的策略。<br>默认值: common.QueryPolicy.SELF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 打印机IP地址 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
