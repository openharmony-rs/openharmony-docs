# writeNdefTag

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## writeNdefTag

```TypeScript
function writeNdefTag(data: string): Promise<void>
```

Writes data to this active tag. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [connectedTag.write](arkts-connectivity-connectedtag-write-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [write](arkts-connectivity-connectedtag-write-f.md)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Data to be written to the active tag. The maximum length is 1024 bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rawData = "010203"; // change it to be correct.
connectedTag.writeNdefTag(rawData).then(() => {
    console.info("connectedTag.writeNdefTag Promise success.");
}).catch((err: BusinessError)=> {
    console.error("connectedTag.writeNdefTag Promise err: " + err);
});
```

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

let rawData = "010203"; // change it to be correct.
connectedTag.writeNdefTag(rawData, (err)=> {
    if (err) {
        console.error("connectedTag.writeNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag.writeNdefTag AsyncCallback success.");
    }
});
```


## writeNdefTag

```TypeScript
function writeNdefTag(data: string, callback: AsyncCallback<void>): void
```

Writes data to this active tag. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [connectedTag.write](arkts-connectivity-connectedtag-write-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [write](arkts-connectivity-connectedtag-write-f.md)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Data to be written to the active tag. The maximum length is 1024 bytes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the active tag content obtained. |

**Examples**

See [writeNdefTag](#writendeftag)
