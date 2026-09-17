# sendMms (System API)

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## sendMms

```TypeScript
function sendMms(context: Context, mmsParams: MmsParams, callback: AsyncCallback<void>): void
```

Sends an MMS message. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.SEND_MESSAGES

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context. <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md). |
| mmsParams | [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md) | Yes | Parameters (including the callback) for sending MMS messages. For details, see [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
FA model:
```

```TypeScript
Stage model:
```


## sendMms

```TypeScript
function sendMms(context: Context, mmsParams: MmsParams): Promise<void>
```

Sends an MMS message. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.SEND_MESSAGES

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context. <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md). |
| mmsParams | [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md) | Yes | Parameters (including the callback) for sending MMS messages. For details, see [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

See [sendMms](#sendmms)
