# offCommunicationStateChange

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## offCommunicationStateChange

```TypeScript
function offCommunicationStateChange(callback: Callback<boolean>, options?: ObserverOptions): void
```

Unsubscribes from the callback for listening to the 5A state.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Telephony.StateRegistry

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates 5A state, and **false** indicates not 5A state. |
| options | [ObserverOptions](arkts-telephony-observer-observeroptions-i.md) | No | Indicates the options for observer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
