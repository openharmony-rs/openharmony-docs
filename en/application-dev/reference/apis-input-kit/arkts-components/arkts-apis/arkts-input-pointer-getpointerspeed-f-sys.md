# getPointerSpeed (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getPointerSpeed

```TypeScript
function getPointerSpeed(callback: AsyncCallback<number>): void
```

Obtains the mouse pointer speed. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the mouse pointer speed. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api.<br>**Applicable version:** 12 and later |

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
            // Obtain the mouse cursor speed.
            pointer.getPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="getpointerspeed-1"></a>

## getPointerSpeed

```TypeScript
function getPointerSpeed(): Promise<number>
```

Obtains the mouse pointer speed. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the mouse pointer speed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api.<br>**Applicable version:** 12 and later |

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
            // Obtain the mouse pointer speed.
            pointer.getPointerSpeed().then(speed => {
              console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
