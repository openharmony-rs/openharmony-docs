# getOptimizationBatteryExclusionApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getOptimizationBatteryExclusionApps

```TypeScript
function getOptimizationBatteryExclusionApps(accountId: number, queryPolicy?: common.QueryPolicy): Array<string>
```

获取电池优化排除列表。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getOptimizationBatteryExclusionApps(accountId: number, queryPolicy?: common.QueryPolicy): Array<string>--><!--Device-applicationManager-function getOptimizationBatteryExclusionApps(accountId: number, queryPolicy?: common.QueryPolicy): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 用户帐号ID。<br>取值应≥0。 |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | 否 | 查询策略。如果不指定该参数，则默认使用了[SELF](arkts-mdm-common-querypolicy-e.md#self)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回电池优化排除列表中的应用包名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
