# getPointerSize (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getPointerSize

```TypeScript
function getPointerSize(callback: AsyncCallback<number>): void
```

Obtains the current mouse pointer size. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **number** is the obtained mouse pointer size (value range: [1-7]). Otherwise, **err** is an error object. |

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
            // Obtain the mouse cursor size.
            pointer.getPointerSize((error: BusinessError, size: number) => {
              if (error) {
                console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="getpointersize-1"></a>

## getPointerSize

```TypeScript
function getPointerSize(): Promise<number>
```

Obtains the current mouse pointer size. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the mouse pointer size. The value ranges from 1 to 7. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |

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
            // Obtain the mouse pointer size.
            pointer.getPointerSize().then((size: number) => {
              console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
