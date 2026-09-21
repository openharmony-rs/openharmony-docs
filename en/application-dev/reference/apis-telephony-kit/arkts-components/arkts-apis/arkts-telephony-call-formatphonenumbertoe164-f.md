# formatPhoneNumberToE164

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## formatPhoneNumberToE164

```TypeScript
function formatPhoneNumberToE164(phoneNumber: string, countryCode: string, callback: AsyncCallback<string>): void
```

Converts a phone number into the E.164 format. This API uses an asynchronous callback to return the result.

The phone number must match the specified country code. For example, for a China phone number, the country code must be **CN**. Otherwise, **null** will be returned.

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number. |
| countryCode | string | Yes | Country code, for example, **CN** (China). All country codes are supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.formatPhoneNumberToE164("138xxxxxxxx", "CN", (err: BusinessError, data: string) => {
    if (err) {
        console.error(`formatPhoneNumberToE164 fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`formatPhoneNumberToE164 success, data->${JSON.stringify(data)}`);
    }
});
```


<a id="formatphonenumbertoe164-1"></a>

## formatPhoneNumberToE164

```TypeScript
function formatPhoneNumberToE164(phoneNumber: string, countryCode: string): Promise<string>
```

Converts a phone number into the E.164 format. This API uses a promise to return the result.

The phone number must match the specified country code. For example, for a China phone number, the country code must be **CN**. Otherwise, **null** will be returned.

All country codes are supported.

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number. |
| countryCode | string | Yes | Country code, for example, **CN** (China). All country codes are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.formatPhoneNumberToE164("138xxxxxxxx", "CN").then((data: string) => {
    console.info(`formatPhoneNumberToE164 success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`formatPhoneNumberToE164 fail, promise: err->${JSON.stringify(err)}`);
});
```
