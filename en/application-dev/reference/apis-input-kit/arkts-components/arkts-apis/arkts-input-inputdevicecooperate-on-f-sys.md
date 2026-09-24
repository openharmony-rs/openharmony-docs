# on (System API)

## Modules to Import

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## on('cooperation')

```TypeScript
function on(type: 'cooperation', callback: AsyncCallback<{ deviceDescriptor: string, eventMsg: EventMsg }>): void
```

Registers a listener for screen hopping state changes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-on-f-sys.md)

**System capability:** SystemCapability.MultimodalInput.Input.Cooperator

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cooperation' | Yes | Event type. The value is **cooperation**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceDescriptor: string, eventMsg: EventMsg }&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, **data** is the screen hopping event information. Otherwise, **err** is undefined. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let callback = (error: BusinessError | undefined, data: { deviceDescriptor: string, eventMsg: EventMsg }) => {
            if (error) {
              console.error(`Failed to monitor cooperation, Code: ${error.code}, message: ${error.message}.`);
              return;
            }
            console.info(`Succeeded in monitoring cooperation, data: ${JSON.stringify(data)}.`);
          };
          try {
            inputDeviceCooperate.on('cooperation', callback);
          } catch (error) {
            console.error(`Failed to register keyboard and mouse traversal status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
