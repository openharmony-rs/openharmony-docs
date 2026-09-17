# getCallState

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## getCallState

```TypeScript
function getCallState(callback: AsyncCallback<CallState>): void
```

Obtains the call status. This API uses an asynchronous callback to return the result.

**Since:** 6

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CallState](arkts-telephony-call-callstate-e.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallState((err: BusinessError, data: call.CallState) => {
    if (err) {
        console.error(`getCallState fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`getCallState success, data->${JSON.stringify(data)}`);
    }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallState().then((data: call.CallState) => {
    console.info(`getCallState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCallState fail, promise: err->${JSON.stringify(err)}`);
});
```


## getCallState

```TypeScript
function getCallState(): Promise<CallState>
```

Obtains the call status. This API uses a promise to return the result.

**Since:** 6

**System capability:** SystemCapability.Telephony.CallManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CallState](arkts-telephony-call-callstate-e.md)&gt; | Promise used to return the result. |

**Examples**

See [getCallState](#getcallstate)
