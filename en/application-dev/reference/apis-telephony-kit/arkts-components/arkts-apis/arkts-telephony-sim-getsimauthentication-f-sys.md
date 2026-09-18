# getSimAuthentication (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimAuthentication

```TypeScript
function getSimAuthentication(slotId: number, authType: AuthType, authData: string): Promise<SimAuthenticationResponse>
```

Performs SIM card authentication.

**Since:** 14

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Sim slot id. |
| authType | [AuthType](arkts-telephony-sim-authtype-e-sys.md) | Yes | The authentication type. |
| authData | string | Yes | Ser password or other authentication information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SimAuthenticationResponse](arkts-telephony-sim-simauthenticationresponse-i-sys.md)&gt; | A string the response of authentication.This value will be null in the following cases: Authentication error, incorrect MAC Authentication error, security context not supported Key freshness failure Authentication error, no memory space available Authentication error, no memory space available in EFMUK. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-failed-to-read-or-update-sim-card-data) | An error occurred when operating the SIM card. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAuthentication(0, sim.AuthType.SIM_AUTH_EAP_SIM_TYPE, "test").then(() => {
    console.info(`getSimAuthentication success.`);
}).catch((err: BusinessError) => {
    console.error(`getSimAuthentication failed, promise: err->${JSON.stringify(err)}`);
});
```
