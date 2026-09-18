# setTouchpadRightClickType (System API)

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setTouchpadRightClickType

```TypeScript
function setTouchpadRightClickType(type: RightClickType, callback: AsyncCallback<void>): void
```

Sets the touchpad right-click menu type. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [RightClickType](arkts-input-pointer-rightclicktype-e.md) | Yes | Touchpad right-click menu type.<br>- TOUCHPAD_RIGHT_BUTTON: Tapping the right-button area of the touchpad. <br>- TOUCHPAD_LEFT_BUTTON: Tapping the left-button area of the touchpad. <br>- TOUCHPAD_TWO_FINGER_TAP: Tapping or pressing the touchpad with two fingers. <br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON&lt;sup&gt;20+&lt;/sup&gt;: Tapping or pressing the touchpad with two fingers, or tapping the right-button area of the touchpad. <br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON&lt;sup&gt;20+&lt;/sup&gt;: Tapping or pressing the touchpad with two fingers, or tapping the left-button area of the touchpad. <br>The default value is **TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

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
            // Set the touchpad right-click type.
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad right click type.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
            // Set the touchpad right-click menu type.
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON).then(() => {
              console.info(`Succeeded in setting touchpad right click type.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## setTouchpadRightClickType

```TypeScript
function setTouchpadRightClickType(type: RightClickType): Promise<void>
```

Sets the touchpad right-click menu type. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [RightClickType](arkts-input-pointer-rightclicktype-e.md) | Yes | Touchpad right-click menu type.<br>- TOUCHPAD_RIGHT_BUTTON: Tapping the right-button area of the touchpad. <br>- TOUCHPAD_LEFT_BUTTON: Tapping the left-button area of the touchpad. <br>- TOUCHPAD_TWO_FINGER_TAP: Tapping or pressing the touchpad with two fingers. <br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON&lt;sup&gt;20+&lt;/sup&gt;: Tapping or pressing the touchpad with two fingers, or tapping the right-button area of the touchpad. <br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON&lt;sup&gt;20+&lt;/sup&gt;: Tapping or pressing the touchpad with two fingers, or tapping the left-button area of the touchpad. <br>The default value is **TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

See [setTouchpadRightClickType](#settouchpadrightclicktype)
