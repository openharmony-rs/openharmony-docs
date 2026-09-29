# onStateChange

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## onStateChange

```TypeScript
function onStateChange(callback: Callback<EthEapStateInfo>): void
```

Subscribes to 802.1X EAP authentication state changes.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function onStateChange(callback: Callback<EthEapStateInfo>): void--><!--Device-eap-function onStateChange(callback: Callback<EthEapStateInfo>): void-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md)&gt; | Yes | Callback used to return EthEapStateInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
