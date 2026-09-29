# offStateChange

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## offStateChange

```TypeScript
function offStateChange(callback?: Callback<EthEapStateInfo>): void
```

Unsubscribes from 802.1X EAP authentication state changes.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function offStateChange(callback?: Callback<EthEapStateInfo>): void--><!--Device-eap-function offStateChange(callback?: Callback<EthEapStateInfo>): void-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md)&gt; | No | Callback used to return EthEapStateInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
