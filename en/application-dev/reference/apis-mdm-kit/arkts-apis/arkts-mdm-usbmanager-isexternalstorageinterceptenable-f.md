# isExternalStorageInterceptEnable

## Modules to Import

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## isExternalStorageInterceptEnable

```TypeScript
function isExternalStorageInterceptEnable(queryPolicy?: common.QueryPolicy): boolean
```

Query the enabling status of external storage device mounting.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_USB

**Model restriction:** This API can be used only in the stage model.

<!--Device-usbManager-function isExternalStorageInterceptEnable(queryPolicy?: common.QueryPolicy): boolean--><!--Device-usbManager-function isExternalStorageInterceptEnable(queryPolicy?: common.QueryPolicy): boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | No | queryPolicy indicates the policy of query.<br>Default value: common.QueryPolicy.SELF. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Enable or disable. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
