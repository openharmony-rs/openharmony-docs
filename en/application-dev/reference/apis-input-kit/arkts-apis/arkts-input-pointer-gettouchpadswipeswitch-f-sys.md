# getTouchpadSwipeSwitch (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getTouchpadSwipeSwitch

```TypeScript
function getTouchpadSwipeSwitch(callback: AsyncCallback<boolean>): void
```

Obtains the touchpad multi-finger swipe switch state. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **state** indicates whether the touchpad multi-finger swipe switch is enabled (**true** indicates yes and **false** indicates no; default value: **true**). Otherwise, **err** is an error object |

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
            // Obtain the touchpad pinch swipe state.
            pointer.getTouchpadSwipeSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="gettouchpadswipeswitch-1"></a>

## getTouchpadSwipeSwitch

```TypeScript
function getTouchpadSwipeSwitch(): Promise<boolean>
```

Obtains the touchpad multi-finger swipe switch state. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the touchpad multi-finger swipe switch is enabled, and **false** indicates that the touchpad multi-finger swipe switch is disabled. The default value is **true**. |

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
            // Obtain the touchpad multi-finger swipe switch state.
            pointer.getTouchpadSwipeSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
