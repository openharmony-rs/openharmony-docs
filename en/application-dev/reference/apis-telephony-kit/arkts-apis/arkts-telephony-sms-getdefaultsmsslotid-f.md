# getDefaultSmsSlotId

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## getDefaultSmsSlotId

```TypeScript
function getDefaultSmsSlotId(callback: AsyncCallback<number>): void
```

Obtains the default slot ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result.

**Since:** 7

**System capability:** SystemCapability.Telephony.SmsMms

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


<a id="getdefaultsmsslotid-1"></a>

## getDefaultSmsSlotId

```TypeScript
function getDefaultSmsSlotId(): Promise<number>
```

Obtains the default slot ID of the SIM card used to send SMS messages. This API uses a promise to return the result.

**Since:** 7

**System capability:** SystemCapability.Telephony.SmsMms

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId().then((data: number) => {
    console.info(`getDefaultSmsSlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```
