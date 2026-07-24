# @ohos.multimodalInput.inputDevice (Input Device) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:23:24.731Z pushedAt=2026-06-12T07:12:55.872Z -->

The **inputDevice** module provides APIs for input device management, including querying input device information, setting/obtaining the keyboard repeat delay, and setting the input device switch status.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.multimodalInput.inputDevice (Input Device)](js-apis-inputdevice.md).

## Modules to Import

```js
import { inputDevice } from '@kit.InputKit';
```

## inputDevice.setKeyboardRepeatDelay<sup>10+</sup>

setKeyboardRepeatDelay(delay: number, callback: AsyncCallback&lt;void&gt;): void

Sets the keyboard repeat delay. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| delay    | number                    | Yes   | Keyboard repeat delay, in ms. The value range is [300, 1000] and the default value is **500**.|
| callback | AsyncCallback&lt;void&gt; | Yes    | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202 | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set Keyboard Repeat Delay
            inputDevice.setKeyboardRepeatDelay(350, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting keyboard repeat delay.`);
            });
          } catch (error) {
            console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatDelay<sup>10+</sup>

setKeyboardRepeatDelay(delay: number): Promise&lt;void&gt;

Sets the keyboard repeat delay. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| delay | number | Yes   | Keyboard repeat delay, in ms. The value range is [300, 1000] and the default value is **500**.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202 | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the key repeat delay to 350 ms
            inputDevice.setKeyboardRepeatDelay(350).then(() => {
              console.info(`Succeeded in setting keyboard repeat delay.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatDelay<sup>10+</sup>

getKeyboardRepeatDelay(callback: AsyncCallback&lt;number&gt;): void

Obtains the keyboard repeat delay. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback   | AsyncCallback&lt;number&gt;                    | Yes    | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the keyboard repeat rate. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtaining the Key Repeat Delay
            inputDevice.getKeyboardRepeatDelay((error: BusinessError, delay: number) => {
              if (error) {
                console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting keyboard repeat delay.`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatDelay<sup>10+</sup>

getKeyboardRepeatDelay(): Promise&lt;number&gt;

Obtains the keyboard repeat delay. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise used to return the keyboard repeat delay.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtaining the Key Repeat Delay
            inputDevice.getKeyboardRepeatDelay().then((delay: number) => {
              console.info(`Succeeded in getting keyboard repeat delay.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatRate<sup>10+</sup>

setKeyboardRepeatRate(rate: number, callback: AsyncCallback&lt;void&gt;): void

Sets the keyboard repeat rate. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| rate    | number                    | Yes   | Keyboard repeat rate, in ms/time. The value range is [36, 100] and the default value is 50.|
| callback | AsyncCallback&lt;void&gt; | Yes    | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Key repeat rate 60ms/time
            inputDevice.setKeyboardRepeatRate(60, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting keyboard repeat rate.`);
            });
          } catch (error) {
            console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatRate<sup>10+</sup>

setKeyboardRepeatRate(rate: number): Promise&lt;void&gt;

Sets the keyboard repeat rate. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name   | Type    | Mandatory  | Description                                 |
| ----- | ------ | ---- | ----------------------------------- |
| rate | number | Yes   | Keyboard repeat rate, in ms/time. The value range is [36, 100] and the default value is 50.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Key repeat rate 60ms/time
            inputDevice.setKeyboardRepeatRate(60).then(() => {
              console.info(`Succeeded in setting keyboard repeat rate.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatRate<sup>10+</sup>

getKeyboardRepeatRate(callback: AsyncCallback&lt;number&gt;): void

Obtains the keyboard repeat rate. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name      | Type                         | Mandatory  | Description            |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | Yes    | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the keyboard repeat rate. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain Key Repeat Rate
            inputDevice.getKeyboardRepeatRate((error: BusinessError, rate: number) => {
              if (error) {
                console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting keyboard repeat rate.`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatRate<sup>10+</sup>

getKeyboardRepeatRate(): Promise&lt;number&gt;

Obtains the keyboard repeat rate. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Return value**

| Type                   | Description                 |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise used to return the keyboard repeat rate.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtaining the Keyboard Repeat Rate
            inputDevice.getKeyboardRepeatRate().then((rate: number) => {
              console.info(`Succeeded in getting keyboard repeat rate.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setInputDeviceEnabled<sup>18+</sup>

setInputDeviceEnabled(deviceId: number, enabled: boolean): Promise&lt;void&gt;

Sets the input switch status of an input device. Take the touchscreen as an example. If the input switch is off, the touchscreen does not respond when being touched. If the input switch is on, the touchscreen wakes up when being touched. This API uses a promise to return the result.

**Required permissions**: ohos.permission.INPUT_DEVICE_CONTROLLER

**System capability**: SystemCapability.MultimodalInput.Input.InputDevice

**System API**: This is a system API.

**Parameters**

| Name  | Type   | Mandatory| Description                     |
| -------- | ------- | ---- | ------------------------- |
| deviceId | number  | Yes  | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.             |
| enabled  | boolean | Yes  | Switch status of the input device. The value **true** indicates that the input device is enabled, and the value **false** indicates the opposite.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Input Device Error Codes](errorcode-inputdevice.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. The application does not have the permission required to call the API |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 3900001  | The specified device does not exist.                         |

**Example**

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the device ID to 0
            inputDevice.setInputDeviceEnabled(0, true).then(() => {
              console.info(`Succeeded in setting input device enabled.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set device enabled, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set device enabled, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```