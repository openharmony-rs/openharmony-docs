# setKeyboardRepeatDelay (System API)

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

<a id="setkeyboardrepeatdelay1"></a>

## setKeyboardRepeatDelay

```TypeScript
function setKeyboardRepeatDelay(delay: number, callback: AsyncCallback<void>): void
```

Sets the keyboard repeat delay. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-inputDevice-function setKeyboardRepeatDelay(delay: int, callback: AsyncCallback<void>): void--><!--Device-inputDevice-function setKeyboardRepeatDelay(delay: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delay | number | Yes | Key repeat delay. Default value: 500 ms. Adjustment range: [300 ms, 1000 ms]. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
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
        });
    }
  }
}
```

<!--DelEnd-->


<a id="setkeyboardrepeatdelay2"></a>

## setKeyboardRepeatDelay

```TypeScript
function setKeyboardRepeatDelay(delay: number): Promise<void>
```

Sets the keyboard repeat delay. This API uses a promise to return the result.

**Since:** 10

<!--Device-inputDevice-function setKeyboardRepeatDelay(delay: int): Promise<void>--><!--Device-inputDevice-function setKeyboardRepeatDelay(delay: int): Promise<void>-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delay | number | Yes | Keyboard key repeat delay. Default value: 500 ms. Adjustment range: [300 ms, 1000 ms]. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
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
              console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

<!--DelEnd-->
