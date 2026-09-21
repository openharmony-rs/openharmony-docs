# off

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## off("notify")

```TypeScript
function off(type: "notify", callback?:Callback<number>): void
```

Unregisters the NFC field strength state events.

**Since:** 8

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | "notify" | Yes | Event type. This parameter has a fixed value of **notify**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the field strength state. If this parameter is not specified, all callbacks associated with the specified event will be unregistered. |

**Examples**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

function nfcStatusCb(rfState: connectedTag.NfcRfType) {
    console.info("connectedTag on Callback rfState: ", rfState);
}

// Process of using an active NFC tag
async function nfcTagTestOn(): Promise<void> {
    try {
        console.info("connectedTag initialize");
        connectedTag.initialize();
    } catch (error) {
        console.error("initialize error:" + error);
    }
    // Register a callback for NFC status change events.
    connectedTag.on("notify", nfcStatusCb);
    try {
        let tag = [3, 1, 0];
        console.info("connectedTag write: tag=" + tag);
        await connectedTag.write(tag);
        let data = await connectedTag.read();
        console.info("connectedTag read: data=" + data);
    } catch (error) {
        console.error("connectedTag error: " + error);
    }
}

// Unregister the callback for NFC status change events and uninitialize the NFC tag.
async function nfcTagTestOff(): Promise<void> {
    // Unregister the callback for NFC status change events.
    connectedTag.off("notify", nfcStatusCb);
    try {
        console.info("connectedTag uninitialize");
        connectedTag.uninitialize();
    } catch (error) {
        console.error("connectedTag error: " + error);
    }
}
```
