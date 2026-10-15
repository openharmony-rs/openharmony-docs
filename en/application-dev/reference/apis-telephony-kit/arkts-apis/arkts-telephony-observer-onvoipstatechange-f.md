# onVoIPStateChange

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## onVoIPStateChange

```TypeScript
function onVoIPStateChange(callback: Callback<VoIPCallStateInfo>): void
```

Callback when the VoIP call state is updated. This callback is invoked when a third-party VoIP application's call state changes and the observer is added to monitor the updates.

**Since:** 26.0.1

**Required permissions:** ohos.permission.MANAGE_CALL_FOR_DEVICES

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-observer-function onVoIPStateChange(callback: Callback<VoIPCallStateInfo>): void--><!--Device-observer-function onVoIPStateChange(callback: Callback<VoIPCallStateInfo>): void-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VoIPCallStateInfo](arkts-telephony-observer-voipcallstateinfo-i.md)&gt; | Yes | Indicates the callback for getting the VoIP call state information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [8800001](../errorcode-telephony.md#8800001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8800002](../errorcode-telephony.md#8800002-service-connection-error) | Service connection failed. |
| [8800003](../errorcode-telephony.md#8800003-system-internal-error) | System internal error. |
