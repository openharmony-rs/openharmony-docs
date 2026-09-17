# readNdefTag

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## readNdefTag

```TypeScript
function readNdefTag(): Promise<string>
```

Reads the content of this active tag. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [read](arkts-connectivity-connectedtag-read-f.md)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the content of the active tag. |

**Examples**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

connectedTag.readNdefTag().then((data) => {
    console.info("connectedTag readNdefTag Promise data = " + data);
}).catch((err: BusinessError)=> {
    console.error("connectedTag readNdefTag Promise err: " + err);
});
```

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

connectedTag.readNdefTag((err, data)=> {
    if (err) {
        console.error("connectedTag readNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag readNdefTag AsyncCallback data: " + data);
    }
});
```


## readNdefTag

```TypeScript
function readNdefTag(callback: AsyncCallback<string>): void
```

Reads the content of this active tag. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [read](arkts-connectivity-connectedtag-read-f.md)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the active tag content obtained. |

**Examples**

See [readNdefTag](#readndeftag)
