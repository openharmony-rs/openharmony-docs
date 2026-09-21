# hasCall

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## hasCall

```TypeScript
function hasCall(callback: AsyncCallback<boolean>): void
```

Checks whether a call is in progress. This API uses an asynchronous callback to return the result.

**Since:** 6

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that a call is in progress, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.hasCall((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`hasCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`hasCall success, data->${JSON.stringify(data)}`);
    }
});
```


<a id="hascall-1"></a>

## hasCall

```TypeScript
function hasCall(): Promise<boolean>
```

Checks whether a call is in progress. This API uses a promise to return the result.

**Since:** 6

**System capability:** SystemCapability.Telephony.CallManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that a call is in progress, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.hasCall().then(() => {
    console.info(`hasCall success`);
}).catch((err: BusinessError) => {
    console.error(`hasCall fail, promise: err->${JSON.stringify(err)}`);
});
```
