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
