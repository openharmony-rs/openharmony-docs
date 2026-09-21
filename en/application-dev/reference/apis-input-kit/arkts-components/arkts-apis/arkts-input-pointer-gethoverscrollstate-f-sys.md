# getHoverScrollState (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getHoverScrollState

```TypeScript
function getHoverScrollState(callback: AsyncCallback<boolean>): void
```

Obtains the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **true** (default) will be returned if the switch is enabled while false will be returned if the switch is disabled. If the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse hover scrolling switch state.
            pointer.getHoverScrollState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="gethoverscrollstate-1"></a>

## getHoverScrollState

```TypeScript
function getHoverScrollState(): Promise<boolean>
```

Obtains the status of the mouse hover scroll switch. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the mouse hover scrolling switch is enabled, and the value **false** indicates that the switch is disabled. The default value is **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Obtain the mouse hover scrolling switch state.
            pointer.getHoverScrollState().then((state: boolean) => {
              console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
