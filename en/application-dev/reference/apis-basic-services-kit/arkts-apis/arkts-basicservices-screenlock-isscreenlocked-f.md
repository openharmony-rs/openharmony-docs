# isScreenLocked

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## isScreenLocked

```TypeScript
function isScreenLocked(callback: AsyncCallback<boolean>): void
```

Checks whether the screen is currently locked.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.MiscServices.ScreenLock

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | the callback of isScreenLocked. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

screenLock.isScreenLocked((err: BusinessError, data: Boolean)=>{      
  if (err) {
    console.error(`Failed to obtain whether the screen is locked, Code: ${err.code}, message: ${err.message}`);
    return;    
  }
  console.info(`Succeeded in Obtaining whether the screen is locked. result: ${data}`);
});
```


<a id="isscreenlocked-1"></a>

## isScreenLocked

```TypeScript
function isScreenLocked(): Promise<boolean>
```

Checks whether the screen is currently locked.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.MiscServices.ScreenLock

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

screenLock.isScreenLocked().then((data: Boolean) => {
  console.info(`Succeeded in Obtaining whether the screen is locked. result: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain whether the screen is locked, Code: ${err.code}, message: ${err.message}`);
});
```
