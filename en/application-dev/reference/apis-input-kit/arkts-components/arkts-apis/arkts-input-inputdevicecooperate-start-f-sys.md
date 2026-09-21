# start (System API)

## Modules to Import

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## start

```TypeScript
function start(sinkDeviceDescriptor: string, srcInputDeviceId: number, callback: AsyncCallback<void>): void
```

Starts screen hopping. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [activateCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-activatecooperate-f-sys.md)

**System capability:** SystemCapability.MultimodalInput.Input.Cooperator

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sinkDeviceDescriptor | string | Yes | Descriptor of the target device for screen hopping. |
| srcInputDeviceId | number | Yes | ID of the target device for screen hopping. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback. If the operation is successful, **err** is **undefined**. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [4400001](../errorcode-cooperator.md#4400001-incorrect-target-device-descriptor) | Incorrect descriptor for the target device. |
| [4400002](../errorcode-cooperator.md#4400002-input-device-operation-failed) | Screen hop failed. |
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
          const sinkDeviceDescriptor = 'descriptor';
          let srcInputDeviceId = 0;
          try {
            inputDeviceCooperate.start(sinkDeviceDescriptor, srcInputDeviceId, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to start keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in starting keyboard mouse crossing.`);
            });
          } catch (error) {
            console.error(`Failed to start keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="start-1"></a>

## start

```TypeScript
function start(sinkDeviceDescriptor: string, srcInputDeviceId: number): Promise<void>
```

Starts screen hopping. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [activateCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-activatecooperate-f-sys.md)

**System capability:** SystemCapability.MultimodalInput.Input.Cooperator

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sinkDeviceDescriptor | string | Yes | Descriptor of the target device for screen hopping. |
| srcInputDeviceId | number | Yes | ID of the target device for screen hopping. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [4400001](../errorcode-cooperator.md#4400001-incorrect-target-device-descriptor) | Incorrect descriptor for the target device. |
| [4400002](../errorcode-cooperator.md#4400002-input-device-operation-failed) | Screen hop failed. |
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
          const sinkDeviceDescriptor = 'descriptor';
          const srcInputDeviceId = 0;
          inputDeviceCooperate.start(sinkDeviceDescriptor, srcInputDeviceId).then(() => {
            console.info(`Succeeded in starting keyboard mouse crossing.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to start keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}
```
