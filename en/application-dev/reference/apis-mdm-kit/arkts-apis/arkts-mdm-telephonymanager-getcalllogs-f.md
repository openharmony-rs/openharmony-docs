# getCallLogs

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## getCallLogs

```TypeScript
function getCallLogs(queryConfig: TelephonyQueryConfig): Promise<Array<CallLogInfo>>
```

Query call records based on the specified time range and phone number. Enterprise MDM applications can use this interface to read device call records for audit. Supports filtering and query by time range and number. The query time range cannot exceed 31 days. The full match mode is used. A maximum of 5000 call records can be stored. When the number of call records exceeds 5000, the earliest call records are automatically deleted. This interface returns the result asynchronously in Promise mode.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_READ_CALL_LOG

**Model restriction:** This API can be used only in the stage model.

<!--Device-telephonyManager-function getCallLogs(queryConfig: TelephonyQueryConfig): Promise<Array<CallLogInfo>>--><!--Device-telephonyManager-function getCallLogs(queryConfig: TelephonyQueryConfig): Promise<Array<CallLogInfo>>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryConfig | [TelephonyQueryConfig](arkts-mdm-telephonymanager-telephonyqueryconfig-i.md) | Yes | Query the configuration, including the time range and phone number. If telephoneNumber is not transferred or is an empty string, all call records within the time range are returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[CallLogInfo](arkts-mdm-telephonymanager-callloginfo-i.md)&gt;&gt; | Promise object, which is used to return the list of call records that meet the query conditions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
