# getOptimizationBatteryExclusionApps

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getOptimizationBatteryExclusionApps

```TypeScript
function getOptimizationBatteryExclusionApps(accountId: number, queryPolicy?: common.QueryPolicy): Array<string>
```

Obtains the battery optimization exclusion list.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-applicationManager-function getOptimizationBatteryExclusionApps(accountId: number, queryPolicy?: common.QueryPolicy): Array<string>--><!--Device-applicationManager-function getOptimizationBatteryExclusionApps(accountId: number, queryPolicy?: common.QueryPolicy): Array<string>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | number | Yes | User account ID. <br>The value must be greater than or equal to 0. |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | No | Query policy. If this parameter is not specified, the default value [SELF](arkts-mdm-common-querypolicy-e.md#self) is used. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns the bundle names of the applications in the exclusion list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
