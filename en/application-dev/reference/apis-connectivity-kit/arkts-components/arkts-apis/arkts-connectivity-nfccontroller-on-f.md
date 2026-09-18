# on

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## on("nfcStateChange")

```TypeScript
function on(type: "nfcStateChange", callback: Callback<NfcState>): void
```

Enables listening for NFC state changes. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "nfcStateChange" | Yes | Event type. The value is **nfcStateChange**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md)&gt; | Yes | Callback used to return the NFC state. |
