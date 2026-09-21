# setPointerVisible

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerVisible

```TypeScript
function setPointerVisible(visible: boolean, callback: AsyncCallback<void>): void
```

Sets whether the mouse pointer is visible in the current window. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visible | boolean | Yes | Whether the mouse pointer is visible in the current window. The value **true** indicates that the mouse pointer is visible, and the value **false** indicates the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported;<br>**Applicable version:** 18 and later |

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
            // Setting Mouse Pointer Visibility
            pointer.setPointerVisible(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer cursor visible, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer cursor visible.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer cursor visible, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        });
    }
  }
}
```


<a id="setpointervisible-1"></a>

## setPointerVisible

```TypeScript
function setPointerVisible(visible: boolean): Promise<void>
```

Sets whether the mouse pointer is visible in the current window. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visible | boolean | Yes | Whether the mouse pointer is visible in the current window. The value **true** indicates that the mouse pointer is visible, and the value **false** indicates the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported;<br>**Applicable version:** 18 and later |

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
            // Setting Mouse Pointer Visibility
            pointer.setPointerVisible(false).then(() => {
              console.info(`Succeeded in setting pointer cursor visible.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer cursor, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer cursor, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
