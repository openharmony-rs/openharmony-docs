# queryIccDiallingNumbers (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## queryIccDiallingNumbers

```TypeScript
function queryIccDiallingNumbers(slotId: number, type: ContactType, callback: AsyncCallback<Array<DiallingNumbersInfo>>): void
```

Query dialing number information on SIM card.

**Since:** 8

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| type | [ContactType](arkts-telephony-sim-contacttype-e-sys.md) | Yes | Indicates contact type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md)&gt;&gt; | Yes | Indicates the callback for getting the dialing number information. |

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

sim.queryIccDiallingNumbers(0, 1, (err: BusinessError, data: Array<sim.DiallingNumbersInfo>) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.queryIccDiallingNumbers(0, 1).then((data:  Array<sim.DiallingNumbersInfo>) => {
    console.info(`queryIccDiallingNumbers success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`queryIccDiallingNumbers failed, promise: err->${JSON.stringify(err)}`);
});
```


## queryIccDiallingNumbers

```TypeScript
function queryIccDiallingNumbers(slotId: number, type: ContactType): Promise<Array<DiallingNumbersInfo>>
```

Query dialing number information on SIM card.

**Since:** 8

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| type | [ContactType](arkts-telephony-sim-contacttype-e-sys.md) | Yes | Indicates contact type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md)&gt;&gt; | Returns the dialing number information. |

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

See [queryIccDiallingNumbers](#queryiccdiallingnumbers)
