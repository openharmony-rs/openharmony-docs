# @ohos.multimodalInput.inputDeviceCooperate (键鼠穿越)(系统接口)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

键鼠穿越功能模块，提供两台或多台设备组网协同后键鼠共享能力，实现键鼠输入设备的跨设备协同操作。

> **说明**
>
>- 本模块接口从API Version 10开始不再维护，从API version 23开始废弃，推荐使用新接口[@ohos.cooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md) (键鼠穿越)。
> 
>- 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>- 本模块接口均为系统接口。

## 导入模块

```ts
import { inputDeviceCooperate } from '@kit.InputKit';
```

## inputDeviceCooperate.enable<sup>(deprecated)</sup>

enable(enable: boolean, callback: AsyncCallback&lt;void&gt;): void

开启、关闭键鼠穿越，使用callback异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.prepareCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperatepreparecooperate11)、[cooperate.unprepareCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperateunpreparecooperate11)替代。

**系统能力**: SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名    | 类型      | 必填  | 说明    |
| -------- | ------------------------- | ---- | --------------------------- |
| enable   | boolean                   | 是   | 键鼠穿越使能状态。 |
| callback | AsyncCallback&lt;void&gt;  | 是  | 回调函数。当开启键鼠穿越成功，err为undefined，否则为错误对象。   |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

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
                console.error(`Failed to enable keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in enabling keyboard mouse crossing.`);
            });
          } catch (error) {
            console.error(`Failed to enable keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.enable<sup>(deprecated)</sup>

enable(enable: boolean): Promise&lt;void&gt;

开启、关闭键鼠穿越，使用Promise异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.prepareCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperatepreparecooperate11-1)、[cooperate.unprepareCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperateunpreparecooperate11-1)替代。

**系统能力**： SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名     | 类型     | 必填  | 说明                                                                                 |
| --------- | ------- | ---- | -------------------------------------------------------------------                 |
| enable    | boolean | 是   | 键鼠穿越使能状态。                   |

**返回值**：

| 类型                 | 说明                     |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt;      | Promise对象，无返回结果。        |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

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
          inputDeviceCooperate.enable(true).then(() => {
            console.info(`Succeeded in enabling keyboard mouse crossing.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to enable keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}
```

## inputDeviceCooperate.start<sup>(deprecated)</sup>

start(sinkDeviceDescriptor: string, srcInputDeviceId: number, callback: AsyncCallback\<void>): void

启动键鼠穿越，使用callback异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.activateCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperateactivatecooperate11)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                          | 必填  | 说明                            |
| --------             | ---------------------------- | ----  | ----------------------------   |
| sinkDeviceDescriptor | string                       |  是   | 键鼠穿越目标设备描述符。             |
| srcInputDeviceId     | number                       |  是   | 键鼠穿越待穿越外设标识符。           |
| callback             | AsyncCallback\<void>         |  是    | 回调函数。当启动键鼠穿越成功，err为undefined，否则为错误对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[键鼠穿越管理错误码](errorcode-cooperator.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 4400001  | Incorrect descriptor for the target device. |
| 4400002  | Screen hop failed. |

**示例**：

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
          const sinkDeviceDescriptor = "descriptor";
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

## inputDeviceCooperate.start<sup>(deprecated)</sup>

start(sinkDeviceDescriptor: string, srcInputDeviceId: number): Promise\<void>

启动键鼠穿越，使用Promise异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.activateCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperateactivatecooperate11-1)替代。

**系统能力**: SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                          | 必填  | 说明                            |
| --------             | ---------------------------- | ----  | ----------------------------   |
| sinkDeviceDescriptor | string                       |  是   | 键鼠穿越目标设备描述符。             |
| srcInputDeviceId     | number                       |  是   | 键鼠穿越待穿越外设标识符。           |



**返回值**：

| 类型                  | 说明                             |
| ---------------------- | ------------------------------- |
| Promise\<void>         | Promise对象，无返回结果。       |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[键鼠穿越管理错误码](errorcode-cooperator.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 4400001  | Incorrect descriptor for the target device. |
| 4400002  | Screen hop failed. |

**示例**：

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
          const sinkDeviceDescriptor = "descriptor";
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

## inputDeviceCooperate.stop<sup>(deprecated)</sup>

stop(callback: AsyncCallback\<void>): void

停止键鼠穿越，使用callback异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.deactivateCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperatedeactivatecooperate11)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                          | 必填  | 说明                            |
| --------             | ---------------------------- | ----  | ----------------------------   |
| callback             | AsyncCallback\<void>         |  是   | 回调函数。当停止键鼠穿越成功，err为undefined，否则为错误对象。        |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

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
                console.error(`Failed to stop keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in stopping keyboard mouse crossing.`);
            });
          } catch (error) {
            console.error(`Failed to stop keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.stop<sup>(deprecated)</sup>

stop(): Promise\<void>

停止键鼠穿越，使用Promise异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.deactivateCooperate](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperatedeactivatecooperate11-1)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**返回值**：

| 类型                | 说明                            |
| --------             | ----------------------------   |
| Promise\<void>       |  Promise对象，无返回结果。      |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |

**示例**：

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
          inputDeviceCooperate.stop().then(() => {
            console.info(`Succeeded in stopping keyboard mouse crossing.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to stop keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}
```

## inputDeviceCooperate.getState<sup>(deprecated)</sup>

getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void

获取键鼠穿越开关的状态，使用callback异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.getCooperateSwitchState](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperategetcooperateswitchstate11)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                          | 必填   | 说明                            |
| --------             | ---------                    | ----  | ----------------------------    |
| deviceDescriptor     | string                       |  是    | 键鼠穿越目标设备描述符。             |
| callback             | AsyncCallback<{ state: boolean }> |  是    | 回调函数。当获取键鼠穿越开关状态成功，err为undefined，data为键鼠穿越开关状态（true表示打开，false表示关闭）；否则为错误对象。        |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**示例**：

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
                console.error(`Failed to get status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting status, data: ${JSON.stringify(data)}.`);
            });
          } catch (error) {
            console.error(`Failed to get status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDeviceCooperate.getState<sup>(deprecated)</sup>

getState(deviceDescriptor: string): Promise<{ state: boolean }>

获取键鼠穿越开关的状态，使用Promise异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.getCooperateSwitchState](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperategetcooperateswitchstate11-1)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                          | 必填   | 说明                            |
| --------             | ---------                    | ----  | ----------------------------    |
| deviceDescriptor     | string                       |  是    | 键鼠穿越目标设备描述符。            |

**返回值**：

| 类型                        | 说明                     |
| -------------------        | ------------------------------- |
| Promise<{ state: boolean }>| Promise对象，返回键鼠穿越开关状态。true表示键鼠穿越开关打开，false表示键鼠穿越开关关闭。       |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**示例**：

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
          inputDeviceCooperate.getState(deviceDescriptor).then((data: object) => {
            console.info(`Succeeded in getting the status, data: ${JSON.stringify(data)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get the status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}
```

## inputDeviceCooperate.on('cooperation')<sup>(deprecated)</sup>

on(type: 'cooperation', callback: AsyncCallback<{ deviceDescriptor: string, eventMsg: EventMsg }>): void

注册监听键鼠穿越状态，使用callback异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.on](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperateoncooperatemessage11)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                                                             | 必填 | 说明                            |
| --------             | ----------------------------                                    | ---- | ----------------------------   |
| type                 | string                                                          |  是  | 注册类型，取值”cooperation“。         |
| callback             | AsyncCallback<{ deviceDescriptor: string, eventMsg: [EventMsg](#eventmsgdeprecated) }> |  是  | 回调函数。当接收键鼠穿越事件成功，err为undefined，data为键鼠穿越事件信息；否则为错误对象。    |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**示例**：

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
            console.info(`Succeeded in monitoring cooperation, msg: ${JSON.stringify(msg)}.`);
            return false;
          }
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

## inputDeviceCooperate.off('cooperation')<sup>(deprecated)</sup>

off(type: 'cooperation', callback?: AsyncCallback\<void>): void

关闭监听键鼠穿越状态，使用callback异步回调。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[cooperate.off](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperateoffcooperatemessage11)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

**参数**：

| 参数名                | 类型                                                              | 必填    | 说明                           |
| --------             | ----------------------------                                     | ----   | ----------------------------   |
| type                 | string                                                           |  是    | 注册类型，取值“cooperation”。         |
| callback             | AsyncCallback\<void> |  否  | 回调函数。当取消注册成功，err为undefined，否则为错误对象。若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 202      | SystemAPI permit error.<br/>适用版本：12+ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**示例**：

```ts
import { inputDeviceCooperate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 取消注册单个回调函数
          let callbackOn = (msg: object) => {
            console.info(`Succeeded in monitoring cooperation, msg: ${JSON.stringify(msg)}.`);
            return false;
          }
          try {
            inputDeviceCooperate.on('cooperation', callbackOn);
            inputDeviceCooperate.off("cooperation", callbackOn);
          } catch (error) {
            console.error(`Failed to unregister callback function, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
          // 取消注册所有回调函数
          let callback = (msg: object) => {
            console.info(`Succeeded in monitoring cooperation, msg: ${JSON.stringify(msg)}.`);
            return false;
          }
          try {
            inputDeviceCooperate.on('cooperation', callback);
            inputDeviceCooperate.off("cooperation");
          } catch (error) {
            console.error(`Failed to unregister callback function, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## EventMsg<sup>(deprecated)</sup>

键鼠穿越事件。

> **说明：**
>
>从 API version 9开始支持，从API version 23开始废弃。建议使用[CooperateMessage](../apis-distributedservice-kit/js-apis-devicestatus-cooperate-sys.md#cooperatemessage11)替代。

**系统能力**：SystemCapability.MultimodalInput.Input.Cooperator

| 名称                       | 值        | 说明                              |
| --------                     | --------- |  -----------------               |
| MSG_COOPERATE_INFO_START     | 200       |  键鼠穿越消息，表示键鼠穿越开始。       |
| MSG_COOPERATE_INFO_SUCCESS   | 201       |  键鼠穿越消息，表示键鼠穿越成功。      |
| MSG_COOPERATE_INFO_FAIL      | 202       |  键鼠穿越消息，表示键鼠穿越失败。      |
| MSG_COOPERATE_STATE_ON       | 500       |  键鼠穿越状态，表示键鼠穿越状态开启。   |
| MSG_COOPERATE_STATE_OFF      | 501       |  键鼠穿越状态，表示键鼠穿越状态关闭。   |
