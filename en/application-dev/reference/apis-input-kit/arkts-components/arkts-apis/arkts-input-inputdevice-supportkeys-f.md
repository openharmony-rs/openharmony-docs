# supportKeys

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## supportKeys

```TypeScript
function supportKeys(deviceId: number, keys: Array<KeyCode>, callback: AsyncCallback<Array<boolean>>): void
```

Queries whether a specified input device supports specified keys. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change. |
| keys | Array&lt;[KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)&gt; | Yes | Keys to be queried. A maximum of five keys can be specified. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;boolean&gt;&gt; | Yes | Callback function. If the query is successful, **err** is **undefined**, and **data** is the key support query result (elements in the array correspond one-to-one to those in **keys**; **true** indicates supported, and **false** indicates not supported). Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // Check whether the input device whose ID is 1 supports keys 17, 22, and 2055.
          try {
            // Querying Key Support
            inputDevice.supportKeys(1, [17, 22, 2055], (error: BusinessError, supportResult: Array<Boolean>) => {
              if (error) {
                console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in querying support keys, supportResult: ${JSON.stringify(supportResult)}.`);
            });
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="supportkeys-1"></a>

## supportKeys

```TypeScript
function supportKeys(deviceId: number, keys: Array<KeyCode>): Promise<Array<boolean>>
```

Checks whether the input device supports the specified keys. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | number | Yes | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change. |
| keys | Array&lt;[KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)&gt; | Yes | Keys to be queried. A maximum of five keys can be specified. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise object, returning the query result. true indicates supported, false indicates not supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // Check whether the input device whose ID is 1 supports keys 17, 22, and 2055.
          try {
            // Querying Key Support
            inputDevice.supportKeys(1, [17, 22, 2055]).then((supportResult: Array<Boolean>) => {
              console.info(`Succeeded in querying support keys, result: ${JSON.stringify(supportResult)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to query support Keys, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
