# unlockScreen

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## unlockScreen

```TypeScript
function unlockScreen(callback: AsyncCallback<void>): void
```

Unlock the screen.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.MiscServices.ScreenLock

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback of unlockScreen. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';

screenLock.unlockScreen((err: BusinessError) => {      
  if (err) {
    console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
    return;    
  }
  console.info(`Succeeded unlocking the screen.`);
});
```

```TypeScript
import { BusinessError } from '@ohos.base';

screenLock.unlockScreen().then(() => {
  console.info('Succeeded unlocking the screen.');
}).catch((err: BusinessError) => {
  console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
});
```


## unlockScreen

```TypeScript
function unlockScreen(): Promise<void>
```

Unlock the screen.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.MiscServices.ScreenLock

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Examples**

See [unlockScreen](#unlockscreen)
