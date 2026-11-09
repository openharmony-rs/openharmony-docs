# getSmsMessages

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## getSmsMessages

```TypeScript
function getSmsMessages(queryConfig: TelephonyQueryConfig): Promise<Array<SmsMessageInfo>>
```

Query SMS messages based on the specified time range and phone number.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_READ_MESSAGES

**Model restriction:** This API can be used only in the stage model.

<!--Device-telephonyManager-function getSmsMessages(queryConfig: TelephonyQueryConfig): Promise<Array<SmsMessageInfo>>--><!--Device-telephonyManager-function getSmsMessages(queryConfig: TelephonyQueryConfig): Promise<Array<SmsMessageInfo>>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryConfig | [TelephonyQueryConfig](arkts-mdm-telephonymanager-telephonyqueryconfig-i.md) | Yes | Query options, including time range and phone number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SmsMessageInfo](arkts-mdm-telephonymanager-smsmessageinfo-i.md)&gt;&gt; | Promise object, which is used to return the list of SMs that meet the query conditions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
