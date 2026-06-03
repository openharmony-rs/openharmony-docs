# @ohos.multimodalInput.inputDevice (输入设备)(系统接口)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

本模块提供输入设备管理能力，包括查询输入设备信息，设置/获取键盘按键重复时延，设置输入设备的开关状态等。

> **说明**：
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含模块的系统接口，其他公开接口请参考[@ohos.multimodalInput.inputDevice (输入设备)](js-apis-inputdevice.md)。


## 导入模块

```js
import { inputDevice } from '@kit.InputKit';
```

## inputDevice.setKeyboardRepeatDelay<sup>10+</sup>

setKeyboardRepeatDelay(delay: number, callback: AsyncCallback&lt;void&gt;): void

设置键盘按键的重复时延，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| delay    | number                    | 是    | 键盘按键重复延迟时间，默认值500ms，调节范围[300ms，1000ms]。 |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。当设置键盘按键重复延迟时间成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202 | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 设置键盘重复延迟
            inputDevice.setKeyboardRepeatDelay(350, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting keyboard repeat delay.`);
            });
          } catch (error) {
            console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatDelay<sup>10+</sup>

setKeyboardRepeatDelay(delay: number): Promise&lt;void&gt;

设置键盘按键的重复时延，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| delay | number | 是    | 键盘按键重复延迟时间，默认值500ms，调节范围[300ms，1000ms]。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202 | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 设置按键重复延迟350ms
            inputDevice.setKeyboardRepeatDelay(350).then(() => {
              console.info(`Succeeded in setting keyboard repeat delay.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatDelay<sup>10+</sup>

getKeyboardRepeatDelay(callback: AsyncCallback&lt;number&gt;): void

获取键盘按键的重复时延，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback   | AsyncCallback&lt;number&gt;                    | 是    | 回调函数。当获取成功，err为undefined，data为键盘按键重复延迟时间；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 获取键盘重复延迟
            inputDevice.getKeyboardRepeatDelay((error: BusinessError, delay: number) => {
              if (error) {
                console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting keyboard repeat delay.`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatDelay<sup>10+</sup>

getKeyboardRepeatDelay(): Promise&lt;number&gt;

获取键盘按键的重复时延，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise对象，返回键盘按键的重复时延。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 获取键盘重复延迟
            inputDevice.getKeyboardRepeatDelay().then((delay: number) => {
              console.info(`Succeeded in getting keyboard repeat delay.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatRate<sup>10+</sup>

setKeyboardRepeatRate(rate: number, callback: AsyncCallback&lt;void&gt;): void

设置键盘按键的重复速率，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| rate    | number                    | 是    | 键盘按键重复速率，默认值50ms/次，调节范围[36ms/次，100ms/次]。 |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。当设置键盘按键重复速率成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 按键重复速率60ms/次
            inputDevice.setKeyboardRepeatRate(60, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting keyboard repeat rate.`);
            });
          } catch (error) {
            console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatRate<sup>10+</sup>

setKeyboardRepeatRate(rate: number): Promise&lt;void&gt;

设置键盘按键的重复速率，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| rate | number | 是    | 键盘按键重复速率，默认值50ms/次，调节范围[36ms/次，100ms/次]。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 按键重复速率60ms/次
            inputDevice.setKeyboardRepeatRate(60).then(() => {
              console.info(`Succeeded in setting keyboard repeat rate.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatRate<sup>10+</sup>

getKeyboardRepeatRate(callback: AsyncCallback&lt;number&gt;): void

获取键盘按键的重复速率，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | 是    | 回调函数。当获取成功，err为undefined，data为键盘按键的重复速率；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 获取键盘重复速率
            inputDevice.getKeyboardRepeatRate((error: BusinessError, rate: number) => {
              if (error) {
                console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting keyboard repeat rate.`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatRate<sup>10+</sup>

getKeyboardRepeatRate(): Promise&lt;number&gt;

获取键盘按键的重复速率，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise&lt;number&gt; | Promise对象，返回键盘按键的重复速率。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 获取键盘重复速率
            inputDevice.getKeyboardRepeatRate().then((rate: number) => {
              console.info(`Succeeded in getting keyboard repeat rate.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get keyboard, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## inputDevice.setInputDeviceEnabled<sup>18+</sup>

setInputDeviceEnabled(deviceId: number, enabled: boolean): Promise&lt;void&gt;

设置输入设备的开关状态。以触摸屏为例：关闭时，点击触摸屏设备不响应；开启时，可正常操作触摸屏。使用Promise异步回调。

**需要权限**：ohos.permission.INPUT_DEVICE_CONTROLLER

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**参数**：

| 参数名   | 类型    | 必填 | 说明                      |
| -------- | ------- | ---- | ------------------------- |
| deviceId | number  | 是   | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。              |
| enabled  | boolean | 是   | 输入设备的开关状态，取值为true表示开启输入设备，取值为false表示关闭输入设备。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[输入设备错误码](errorcode-inputdevice.md)。


| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. The application does not have the permission required to call the API |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 3900001  | The specified device does not exist.                         |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 设置设备ID为0
            inputDevice.setInputDeviceEnabled(0, true).then(() => {
              console.info(`Succeeded in setting input device enabled.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set device enable, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set device enable, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
