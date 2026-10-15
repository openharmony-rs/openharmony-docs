# isScreenLocked

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

<a id="isscreenlocked1"></a>

## isScreenLocked

```TypeScript
function isScreenLocked(callback: AsyncCallback<boolean>): void
```

Checks whether the screen is currently locked.

**Since:** 7

**Deprecated since:** 9

<!--Device-screenLock-function isScreenLocked(callback: AsyncCallback<boolean>): void--><!--Device-screenLock-function isScreenLocked(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | the callback of isScreenLocked. |

**Examples**

ArkTS Example:

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

JS Example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="text-content" on:click="isScreenLocked">Tap to call isScreenLocked</text>
    <text class="text-content">result: "{{ test_val }}"</text>
</div>
```

```TypeScript
/* xxx.css */
.container {
    width: 100%;
    height: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: aqua;
}
.text-content {
    color: black;
    font-size: 28fp;
    width: 100%;
    text-align: left;
    margin-top: 20px;
    padding-left: 50px;
    padding-right: 50px;
}
```

```TypeScript
// xxx.js
import screenLock from '@ohos.screenLock';

export default {
    data: {
        test_val: 'not called'
    },
    isScreenLocked() {
        this.test_val = 'start calling isScreenLocked';
        try {
            screenLock.isScreenLocked((err, data) => {
                if (err) {
                    this.test_val = `isScreenLocked error: ${err.code}, message: ${err.message}`;
                    console.error(`Failed to obtain whether the screen is locked, Code: ${err.code}, message: ${err.message}`);
                    return;
                }
                this.test_val = `isScreenLocked success: ${data}`;
                console.info(`Succeeded in Obtaining whether the screen is locked. result: ${data}`);
            });
        } catch (err) {
            this.test_val = `isScreenLocked exception: ${err.code} ${err.message}`;
        }
    }
}
```


<a id="isscreenlocked2"></a>

## isScreenLocked

```TypeScript
function isScreenLocked(): Promise<boolean>
```

Checks whether the screen is currently locked.

**Since:** 7

**Deprecated since:** 9

<!--Device-screenLock-function isScreenLocked(): Promise<boolean>--><!--Device-screenLock-function isScreenLocked(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Examples**

ArkTS Example:

```TypeScript
import { BusinessError } from '@ohos.base';

screenLock.isScreenLocked().then((data: Boolean) => {
  console.info(`Succeeded in Obtaining whether the screen is locked. result: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain whether the screen is locked, Code: ${err.code}, message: ${err.message}`);
});
```
