# getNROptionMode (System API)

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getNROptionMode

```TypeScript
function getNROptionMode(slotId: number, callback: AsyncCallback<NROptionMode>): void
```

Get the option mode of NR.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NROptionMode](arkts-telephony-radio-nroptionmode-e-sys.md)&gt; | Yes | Indicates the callback for getting the selection mode of NR. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNROptionMode(slotId, (err: BusinessError, data: radio.NROptionMode) => {
    if (err) {
        console.error(`getNROptionMode failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getNROptionMode success, callback: data->${JSON.stringify(data)}`);
});
```


<a id="getnroptionmode-1"></a>

## getNROptionMode

```TypeScript
function getNROptionMode(slotId: number): Promise<NROptionMode>
```

Get the option mode of NR.

**Since:** 10

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NROptionMode](arkts-telephony-radio-nroptionmode-e-sys.md)&gt; | Returns the selection mode of NR. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNROptionMode(slotId).then((data: radio.NROptionMode) => {
    console.info(`getNROptionMode success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getNROptionMode failed, promise: err->${JSON.stringify(err)}`);
});
```
