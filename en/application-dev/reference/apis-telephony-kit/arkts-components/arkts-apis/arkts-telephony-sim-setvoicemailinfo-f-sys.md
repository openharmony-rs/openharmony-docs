# setVoiceMailInfo (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## setVoiceMailInfo

```TypeScript
function setVoiceMailInfo(slotId: number, mailName: string, mailNumber: string, callback: AsyncCallback<void>): void
```

Sets the voice mail information.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from `0` to the maximum card slot index number supported by the device. |
| mailName | string | Yes | Indicates the name of voice mail. |
| mailNumber | string | Yes | Indicates the number of voice mail. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setVoiceMailInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-failed-to-read-or-update-sim-card-data) | The SIM card failed to read or update data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.setVoiceMailInfo(0, "mail", "xxx@xxx.com", (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}`);
});
```


<a id="setvoicemailinfo-1"></a>

## setVoiceMailInfo

```TypeScript
function setVoiceMailInfo(slotId: number, mailName: string, mailNumber: string): Promise<void>
```

Sets the voice mail information.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from `0` to the maximum card slot index number supported by the device. |
| mailName | string | Yes | Indicates the name of voice mail. |
| mailNumber | string | Yes | Indicates the number of voice mail. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setVoiceMailInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-failed-to-read-or-update-sim-card-data) | The SIM card failed to read or update data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.setVoiceMailInfo(0, "mail", "xxx@xxx.com").then(() => {
    console.info(`setVoiceMailInfo success.`);
}).catch((err: BusinessError) => {
    console.error(`setVoiceMailInfo failed, promise: err->${JSON.stringify(err)}`);
});
```
