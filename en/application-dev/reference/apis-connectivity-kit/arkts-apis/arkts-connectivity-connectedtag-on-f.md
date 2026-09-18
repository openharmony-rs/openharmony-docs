# on

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## on("notify")

```TypeScript
function on(type: "notify", callback: Callback<number>): void
```

Registers the NFC field strength state events.

**Since:** 8

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "notify" | Yes | Event type. This parameter has a fixed value of **notify**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the [NfcRfType](arkts-connectivity-connectedtag-nfcrftype-e.md). |
