# @ohos.screenLock (Screen Lock)
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @jiayunpeng2-->
<!--Designer: @yaoruijiang-->
<!--Tester: @dyx118186878-->
<!--Adviser: @fang-jinxu-->

The **screenlock** module is a system module in OpenHarmony. It provides APIs for screen lock applications to subscribe to screen lock status changes as well as callbacks for them to receive the results. It also provides APIs for third-party applications to unlock the screen, obtain the screen locked status, and check whether a lock screen password has been set.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - In the content below, for the Lite Wearable device type, refer to "JS Example"; for other device types that support this module, refer to "ArkTS Example".

## Modules to Import

ArkTS Example:

```ts
import screenLock from '@ohos.screenLock';
```

JS Example:

```js
import screenLock from '@ohos.screenLock';
```

## screenLock.isScreenLocked<sup>(deprecated)</sup>

isScreenLocked(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the screen is locked. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9 on devices, except for lite wearables. The substitute API is available only for system applications.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Parameters**

| Name     | Type                         | Mandatory | Description                                                  |
| -------- | ---------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;boolean&gt; | Yes       | Callback used to return the result. The value **true** means that the screen is locked, and **false** means the opposite. |

**Example**

ArkTS Example:

  ```ts
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

  ```xml
  <!-- xxx.hml -->
  <div class="container">
      <text class="text-content" on:click="isScreenLocked">Tap to call isScreenLocked</text>
      <text class="text-content">result: "{{ test_val }}"</text>
  </div>
  ```

  ```css
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

  ```js
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

## screenLock.isScreenLocked<sup>(deprecated)</sup>

isScreenLocked(): Promise&lt;boolean&gt;

Checks whether the screen is locked. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9 on devices, except for lite wearables.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Return value**

| Type                   | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the screen is locked, and **false** means the opposite. |

**Example**

ArkTS Example:

  ```ts
  import { BusinessError } from '@ohos.base';

  screenLock.isScreenLocked().then((data: Boolean) => {
    console.info(`Succeeded in Obtaining whether the screen is locked. result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain whether the screen is locked, Code: ${err.code}, message: ${err.message}`);
  });
  ```

> **NOTE**
> Lite Wearable does not support ES6 syntax such as Promise/async/await. Use the callback form of the API  instead.

## screenLock.isSecureMode<sup>(deprecated)</sup>

isSecureMode(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the device is in secure mode. When the device is in secure mode, its screen requires a password, unlock pattern, or other user credentials to unlock. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9 on devices, except for lite wearables.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Parameters**

| Name     | Type                         | Mandatory | Description                                                  |
| -------- | ---------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;boolean&gt; | Yes       | Callback used to return the result. The value **true** means that the device is in secure mode, and **false** means the opposite. |

**Example**

ArkTS Example:

  ```ts
  import { BusinessError } from '@ohos.base';

  screenLock.isSecureMode((err: BusinessError, data: Boolean)=>{
    if (err) {
      console.error(`Failed to obtain whether the device is in secure mode, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in Obtaining whether the device is in secure mode. result: ${data}`);
  });
  ```

JS Example:

  ```xml
  <!-- xxx.hml -->
  <div class="container">
      <text class="text-content" on:click="isSecureMode">Tap to call isSecureMode</text>
      <text class="text-content">result: "{{ test_val }}"</text>
  </div>
  ```

  ```css
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

  ```js
  // xxx.js
  import screenLock from '@ohos.screenLock';

  export default {
      data: {
          test_val: 'not called'
      },
      isSecureMode() {
          this.test_val = 'start calling isSecureMode';
          try {
              screenLock.isSecureMode((err, data) => {
                  if (err) {
                      this.test_val = `isSecureMode error: ${err.code}, message: ${err.message}`;
                      console.error(`Failed to obtain whether the device is in secure mode, Code: ${err.code}, message: ${err.message}`);
                      return;
                  }
                  this.test_val = `isSecureMode success: ${data}`;
                  console.info(`Succeeded in Obtaining whether the device is in secure mode. result: ${data}`);
              });
          } catch (err) {
              this.test_val = `isSecureMode exception: ${err.code} ${err.message}`;
          }
      }
  }
  ```

## screenLock.isSecureMode<sup>(deprecated)</sup>

isSecureMode(): Promise&lt;boolean&gt;

Checks whether the device is in secure mode. When the device is in secure mode, its screen requires a password, unlock pattern, or other user credentials to unlock. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9 on devices, except for lite wearables.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Return value**

| Type                   | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the device is in secure mode, and **false** means the opposite. |

**Example**

ArkTS Example:

  ```ts
  import { BusinessError } from '@ohos.base';

  screenLock.isSecureMode().then((data: Boolean) => {
    console.info(`Succeeded in Obtaining whether the device is in secure mode. result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain whether the device is in secure mode, Code: ${err.code}, message: ${err.message}`);
  });
  ```

> **NOTE**
> Lite Wearable does not support ES6 syntax such as Promise/async/await. Use the callback form of the API instead.

## screenLock.unlockScreen<sup>(deprecated)</sup>

unlockScreen(callback: AsyncCallback&lt;void&gt;): void

Unlocks the screen. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9 on devices, except for lite wearables.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Parameters**

| Name     | Type                      | Mandatory | Description                                                  |
| -------- | ------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;void&gt; | Yes       | Callback used to return the result. If the screen is unlocked successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Example**

ArkTS Example:

  ```ts
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

  ```xml
  <!-- xxx.hml -->
  <div class="container">
      <text class="text-content" on:click="unlockScreen">Tap to call unlockScreen</text>
      <text class="text-content">result: "{{ test_val }}"</text>
  </div>
  ```

  ```css
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

  ```js
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

## screenLock.unlockScreen<sup>(deprecated)</sup>

unlockScreen(): Promise&lt;void&gt;

Unlocks the screen. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9 on devices, except for lite wearables.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Return value**

| Type                | Description                    |
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

ArkTS Example:

  ```ts
  import { BusinessError } from '@ohos.base';

  screenLock.unlockScreen().then(() => {
    console.info('Succeeded unlocking the screen.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
  });
  ```

> **NOTE**
> Lite Wearable does not support ES6 syntax such as Promise/async/await. Use the callback form of the API ([unlockScreen(callback)](#screenLockunlockscreendeprecated)) instead.