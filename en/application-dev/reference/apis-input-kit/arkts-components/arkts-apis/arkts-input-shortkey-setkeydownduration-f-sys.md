# setKeyDownDuration (System API)

## Modules to Import

```TypeScript
import { shortKey } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';
```

## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: number, callback: AsyncCallback<void>): void
```

Sets the delay for starting an ability using shortcut keys. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.ShortKey

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| businessKey | string | Yes | Unique service ID registered on the multimodal side. It corresponds to **businessId** in the **ability_launch_config.json** file. You need to query this parameter on your own before calling the API. |
| delay | number | Yes | Delay for starting an ability using shortcut keys, in milliseconds. This field is valid only when shortcut keys are pressed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { shortKey } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the delay for starting the ability to 500 ms.
            shortKey.setKeyDownDuration('businessId', 500, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting key down duration.`);
            });
          } catch (error) {
            console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        });
    }
  }
}
```


<a id="setkeydownduration-1"></a>

## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: number): Promise<void>
```

Sets the delay for starting an ability using shortcut keys. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.ShortKey

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| businessKey | string | Yes | Unique service ID registered on the multimodal side. It corresponds to **businessId** in the **ability_launch_config.json** file. You need to query this parameter on your own before calling the API. |
| delay | number | Yes | Delay for starting an ability using shortcut keys, in milliseconds. This field is valid only when shortcut keys are pressed. |

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

```TypeScript
import { shortKey } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the delay for starting the ability to 500 ms.
            shortKey.setKeyDownDuration('businessId', 500).then(() => {
              console.info(`Succeeded in setting key down duration.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
