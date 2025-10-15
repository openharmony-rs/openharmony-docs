# @ohos.multimodalInput.inputDeviceCooperate (Screen Hopping) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

The **inputDeviceCooperate** module implements screen hopping for two or more networked devices to share the keyboard and mouse for collaborative operations.

> **NOTE**
>
>- The APIs provided by this module are no longer maintained since API Version 10. You are advised to use [@ohos.cooperate (Screen Hopping)](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md).
> 
>- The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>- The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
```

## inputDeviceCooperate.enable

enable(enable: boolean, callback: AsyncCallback&lt;void&gt;): void

Specifies whether to enable screen hopping. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name   | Type     | Mandatory | Description   |
| -------- | ------------------------- | ---- | --------------------------- |
| enable   | boolean                   | Yes  | Whether to enable screen hopping.|
| callback | AsyncCallback&lt;void&gt;  | Yes |Callback used to return the result.  |

**Error codes**

For details about the following error codes, see [Screen Hopping Error Codes](../apis-distributedservice-kit/errorcode-devicestatus.md).

| ID| Error Message         |
| -------- | -----------------|
| 401 | Parameter error.      |


**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDeviceCooperate.enable(true, (error: BusinessError) => {
              if (error) {
                console.error(`Keyboard mouse crossing enable failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Keyboard mouse crossing enable success.`);
            });
          } catch (error) {
            console.error(`Keyboard mouse crossing enable failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.enable

enable(enable: boolean): Promise&lt;void&gt;

Specifies whether to enable screen hopping. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name    | Type    | Mandatory | Description                                                                                |
| --------- | ------- | ---- | -------------------------------------------------------------------                 |
| enable    | boolean | Yes  | Whether to enable screen hopping.                  |

**Return value**

| Type                | Description                    |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt;      | Promise that returns no value.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | -----------------|
| 401 | Parameter error.      |

**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDeviceCooperate.enable(true).then(() => {
              console.info(`Keyboard mouse crossing enable success.`);
            }, (error: BusinessError) => {
              console.error(`Keyboard mouse crossing enable failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            });
          } catch (error) {
            console.error(`Keyboard mouse crossing enable failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.start

start(sinkDeviceDescriptor: string, srcInputDeviceId: number, callback: AsyncCallback\<void>): void

Starts screen hopping. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                         | Mandatory | Description                           |
| --------             | ---------------------------- | ----  | ----------------------------   |
| sinkDeviceDescriptor | string                       |  Yes  | Descriptor of the target device for screen hopping.            |
| srcInputDeviceId     | number                       |  Yes  | ID of the target device for screen hopping.          |
| callback             | AsyncCallback\<void>         |  Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Hopping Error Codes](errorcode-cooperator.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401      | Parameter error.    |
| 4400001  | Incorrect descriptor for the target device.                |
| 4400002  | Screen hop failed.   |

**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let sinkDeviceDescriptor = "descriptor";
          let srcInputDeviceId = 0;
          try {
            inputDeviceCooperate.start(sinkDeviceDescriptor, srcInputDeviceId, (error: BusinessError) => {
              if (error) {
                console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Start Keyboard mouse crossing success.`);
            });
          } catch (error) {
            console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.start

start(sinkDeviceDescriptor: string, srcInputDeviceId: number): Promise\<void>

Starts screen hopping. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                         | Mandatory | Description                           |
| --------             | ---------------------------- | ----  | ----------------------------   |
| sinkDeviceDescriptor | string                       |  Yes  | Descriptor of the target device for screen hopping.            |
| srcInputDeviceId     | number                       |  Yes  | ID of the target device for screen hopping.          |



**Return value**

| Type                 | Description                            |
| ---------------------- | ------------------------------- |
| Promise\<void>         | Promise used to return the result.      |

**Error codes**

For details about the error codes, see [Screen Hopping Error Codes](errorcode-cooperator.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401      | Parameter error.    |
| 4400001  | Incorrect descriptor for the target device.          |
| 4400002  | Screen hop failed.              |

**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let sinkDeviceDescriptor = "descriptor";
          let srcInputDeviceId = 0;
          try {
            inputDeviceCooperate.start(sinkDeviceDescriptor, srcInputDeviceId).then(() => {
              console.info(`Start Keyboard mouse crossing success.`);
            }, (error: BusinessError) => {
              console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            });
          } catch (error) {
            console.error(`Start Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.stop

stop(callback: AsyncCallback\<void>): void

Stops screen hopping. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                         | Mandatory | Description                           |
| --------             | ---------------------------- | ----  | ----------------------------   |
| callback             | AsyncCallback\<void>         |  Yes  | Callback used to return the result.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ----------------- |
| 401      | Parameter error.  |

**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDeviceCooperate.stop((error: BusinessError) => {
              if (error) {
                console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Stop Keyboard mouse crossing success.`);
            });
          } catch (error) {
            console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.stop

stop(): Promise\<void>

Stops screen hopping. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Return value**

| Type               | Description                           |
| --------             | ----------------------------   |
| Promise\<void>       |  Promise used to return the result.     |

**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDeviceCooperate.stop().then(() => {
              console.info(`Stop Keyboard mouse crossing success.`);
            }, (error: BusinessError) => {
              console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            });
          } catch (error) {
            console.error(`Stop Keyboard mouse crossing failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.getState

getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void

Checks whether screen hopping is enabled. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                         | Mandatory  | Description                           |
| --------             | ---------                    | ----  | ----------------------------    |
| deviceDescriptor     | string                       |  Yes   | Descriptor of the target device for screen hopping.            |
| callback             | AsyncCallback<{ state: boolean }> |  Yes   | Callback used to return the result.       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 401      | Parameter error.  |


**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let deviceDescriptor = "descriptor";
          try {
            inputDeviceCooperate.getState(deviceDescriptor, (error: BusinessError, data: object) => {
              if (error) {
                console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Get the status success, data: ${JSON.stringify(data)}`);
            });
          } catch (error) {
            console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.getState

getState(deviceDescriptor: string): Promise<{ state: boolean }>

Checks whether screen hopping is enabled. This API uses a promise to return the result.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                         | Mandatory  | Description                           |
| --------             | ---------                    | ----  | ----------------------------    |
| deviceDescriptor     | string                       |  Yes   | Descriptor of the target device for screen hopping.           |

**Return value**

| Type                       | Description                    |
| -------------------        | ------------------------------- |
| Promise<{ state: boolean }>| Promise used to return the result. The value **true** indicates that screen hopping is enabled, and the **false** indicates the opposite.      |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 401      | Parameter error.  |


**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let deviceDescriptor = "descriptor";
          try {
            inputDeviceCooperate.getState(deviceDescriptor).then((data: object) => {
              console.info(`Get the status success, data: ${JSON.stringify(data)}`);
            }, (error: BusinessError) => {
              console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            });
          } catch (error) {
            console.error(`Get the status failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## on('cooperation')

on(type: 'cooperation', callback: AsyncCallback<{ deviceDescriptor: string, eventMsg: EventMsg }>): void

Enables listening for screen hopping status change events.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                                                            | Mandatory| Description                           |
| --------             | ----------------------------                                    | ---- | ----------------------------   |
| type                 | string                                                          |  Yes | Event type. The value is **cooperation**.        |
| callback             | AsyncCallback<{ deviceDescriptor: string, eventMsg: [EventMsg](#eventmsg) }> |  Yes | Callback used to return the result.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 401      | Parameter error.  |


**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let callback = (msg: object) => {
            console.info(`Keyboard mouse crossing event: ${JSON.stringify(msg)}`);
            return false;
          }
          try {
            inputDeviceCooperate.on('cooperation', callback);
          } catch (error) {
            console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## off('cooperation')

off(type: 'cooperation', callback?: AsyncCallback\<void>): void

Disables listening for screen hopping status change events.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

**Parameters**

| Name               | Type                                                             | Mandatory   | Description                          |
| --------             | ----------------------------                                     | ----   | ----------------------------   |
| type                 | string                                                           |  Yes   | Event type. The value is **cooperation**.        |
| callback             | AsyncCallback\<void> |  No | Callback to be unregistered. If this parameter is not specified, all callbacks registered by the current application will be unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 401      | Parameter error.  |


**Example**

```ts
import { inputDeviceCooperate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Unregister a single callback.
          let callbackOn = (msg: object) => {
            console.info(`Keyboard mouse crossing event: ${JSON.stringify(msg)}`);
            return false;
          }
          let callbackOff = () => {
            console.info(`Keyboard mouse crossing event`);
            return false;
          }
          try {
            inputDeviceCooperate.on('cooperation', callbackOn);
            inputDeviceCooperate.off("cooperation", callbackOff);
          } catch (error) {
            console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```
```ts
import { inputDeviceCooperate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // Unregister all callbacks.
          let callback = (msg: object) => {
            console.info(`Keyboard mouse crossing event: ${JSON.stringify(msg)}`);
            return false;
          }
          try {
            inputDeviceCooperate.on('cooperation', callback);
            inputDeviceCooperate.off("cooperation");
          } catch (error) {
            console.error(`Execute failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## EventMsg

Enumerates screen hopping event.

**System capability**: SystemCapability.MultimodalInput.Input.Cooperator

| Name                      | Value       | Description                             |
| --------                     | --------- |  -----------------               |
| MSG_COOPERATE_INFO_START     | 200       |  Screen hopping starts.      |
| MSG_COOPERATE_INFO_SUCCESS   | 201       |  Screen hopping succeeds.     |
| MSG_COOPERATE_INFO_FAIL      | 202       |  Screen hopping fails.     |
| MSG_COOPERATE_STATE_ON       | 500       |  Screen hopping is enabled.  |
| MSG_COOPERATE_STATE_OFF      | 501       |  Screen hopping is disabled.  |
