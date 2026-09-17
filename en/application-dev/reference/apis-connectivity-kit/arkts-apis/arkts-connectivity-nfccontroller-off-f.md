# off

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## off("nfcStateChange")

```TypeScript
function off(type: "nfcStateChange", callback?: Callback<NfcState>): void
```

Unsubscribes from the NFC state changes. Upon successful unsubscription, the subscriber will not receive NFC state change notifications. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "nfcStateChange" | Yes | Event type. The value is **nfcStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md)&gt; | No | Callback for the NFC state changes. This parameter can be left blank. If this parameter is not specified, this API unregisters all callbacks for the specified event. |
