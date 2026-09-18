# dial

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## dial

```TypeScript
function dial(phoneNumber: string, options: DialOptions, callback: AsyncCallback<boolean>): void
```

Initiates a call. You can set call options as needed. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 9. The substitute API is available
> only for system applications.

**Since:** 6

**Deprecated since:** 9

**Required permissions:** ohos.permission.PLACE_CALL

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number. |
| options | [DialOptions](arkts-telephony-call-dialoptions-i.md) | Yes | Call option, which indicates whether the call is a voice call or video call. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.dial("138xxxxxxxx", (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let dialOptions: call.DialOptions = {
    extras: false
}
call.dial("138xxxxxxxx", dialOptions, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let dialOptions: call.DialOptions = {
    extras: false
}
call.dial("138xxxxxxxx", dialOptions).then((data: boolean) => {
    console.info(`dial success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`dial fail, promise: err->${JSON.stringify(err)}`);
});
```


## dial

```TypeScript
function dial(phoneNumber: string, options?: DialOptions): Promise<boolean>
```

Initiates a call. You can set call options as needed. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 9. The substitute API is available
> only for system applications.

**Since:** 6

**Deprecated since:** 9

**Required permissions:** ohos.permission.PLACE_CALL

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number. |
| options | [DialOptions](arkts-telephony-call-dialoptions-i.md) | No | Call option, which indicates whether the call is a voice call or video call. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Examples**

See [dial](#dial)


## dial

```TypeScript
function dial(phoneNumber: string, callback: AsyncCallback<boolean>): void
```

Initiates a call. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 9. The substitute API is available
> only for system applications.

**Since:** 6

**Deprecated since:** 9

**Required permissions:** ohos.permission.PLACE_CALL

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Phone number. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Examples**

See [dial](#dial)
