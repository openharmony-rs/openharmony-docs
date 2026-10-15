# unlockScreen

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

<a id="unlockscreen1"></a>

## unlockScreen

```TypeScript
function unlockScreen(callback: AsyncCallback<void>): void
```

Unlock the screen.

**Since:** 7

**Deprecated since:** 9

<!--Device-screenLock-function unlockScreen(callback: AsyncCallback<void>): void--><!--Device-screenLock-function unlockScreen(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback of unlockScreen. |

**Examples**

ArkTS Example:

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

JS Example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <text class="text-content" on:click="unlockScreen">Tap to call unlockScreen</text>
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
    unlockScreen() {
        this.test_val = 'start calling unlockScreen';
        try {
            screenLock.unlockScreen((err) => {
                if (err) {
                    this.test_val = `unlockScreen error: ${err.code}, message: ${err.message}`;
                    console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
                    return;
                }
                this.test_val = `unlockScreen success`;
                console.info(`Succeeded unlocking the screen.`);
            });
        } catch (err) {
            this.test_val = `unlockScreen exception: ${err.code} ${err.message}`;
        }
    }
}
```


<a id="unlockscreen2"></a>

## unlockScreen

```TypeScript
function unlockScreen(): Promise<void>
```

Unlock the screen.

**Since:** 7

**Deprecated since:** 9

<!--Device-screenLock-function unlockScreen(): Promise<void>--><!--Device-screenLock-function unlockScreen(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Examples**

ArkTS Example:

```TypeScript
import { BusinessError } from '@ohos.base';

screenLock.unlockScreen().then(() => {
  console.info('Succeeded unlocking the screen.');
}).catch((err: BusinessError) => {
  console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
});
```
