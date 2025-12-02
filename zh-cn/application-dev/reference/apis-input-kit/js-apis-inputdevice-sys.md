# @ohos.multimodalInput.inputDevice (输入设备)(系统接口)


本模块提供输入设备管理能力，包括查询输入设备信息等。


> **说明**：
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含模块的系统接口，其他公开接口请参考[@ohos.multimodalInput.inputDevice (输入设备)](js-apis-inputdevice.md)。


## 导入模块

```js
import { inputDevice } from '@kit.InputKit';
```

## inputDevice.setKeyboardRepeatDelay<sup>10+</sup>

ArkTS-Dyn: setKeyboardRepeatDelay(delay: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta:  setKeyboardRepeatDelay(delay: int, callback: AsyncCallback&lt;void&gt;): void

设置键盘按键的重复时延，使用Callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| delay    | ArkTS-Dyn: number<br/>ArkTS-Sta: int                    | 是    | 键盘按键重复延迟时间，默认值500ms，调节范围[300ms，1000ms]。 |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202 | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Dyn示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setKeyboardRepeatDelay(350, (error: Error) => {
              if (error) {
                console.error(`Set keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Set keyboard repeat delay success`);
            });
          } catch (error) {
            console.error(`Set keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let fnCallBack = (err: BusinessError<void>|null, data: undefined)  => {
              if (error) {
                console.error(`Set keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Set keyboard repeat delay success`);
            }
            inputDevice.setKeyboardRepeatDelay(350, fnCallBack);
          } catch (error) {
            console.error(`Set keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatDelay<sup>10+</sup>

ArkTS-Dyn: setKeyboardRepeatDelay(delay: number): Promise&lt;void&gt;

ArkTS-Sta: setKeyboardRepeatDelay(delay: int): Promise&lt;void&gt;

设置键盘按键的重复时延，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| delay | ArkTS-Dyn: number <br> ArkTS-Sta: int  | 是    | 键盘按键重复延迟时间，默认值500ms，调节范围[300ms，1000ms]。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202 | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setKeyboardRepeatDelay(350).then(() => {
              console.log(`Set keyboard repeat delay success`);
            });
          } catch (error) {
            console.error(`Set keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatDelay<sup>10+</sup>

ArkTS-Dyn: getKeyboardRepeatDelay(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getKeyboardRepeatDelay(callback: AsyncCallback&lt;int&gt;): void

获取键盘按键的重复时延，使用Callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback   | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;int&gt;                | 是    | 回调函数，返回键盘按键重复延迟时间。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Dyn示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatDelay((error: Error, delay: Number) => {
              if (error) {
                console.error(`Get keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Get keyboard repeat delay success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let fnCallBack = (err: BusinessError<void>|null, delay: int|undefined) => {
               if (error) {
                console.error(`Get keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Get keyboard repeat delay success`);
            };
            inputDevice.getKeyboardRepeatDelay(fnCallBack);
          } catch (error) {
            console.error(`Get keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatDelay<sup>10+</sup>

ArkTS-Dyn: getKeyboardRepeatDelay(): Promise&lt;number&gt;

ArkTS-Sta: getKeyboardRepeatDelay(): Promise&lt;int&gt;

获取键盘按键的重复时延，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt; <br> ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回键盘按键的重复时延。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Dyn示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatDelay().then((delay: Number) => {
              console.log(`Get keyboard repeat delay success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatDelay().then((delay: int) => {
              console.log(`Get keyboard repeat delay success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat delay failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatRate<sup>10+</sup>

ArkTS-Dyn: setKeyboardRepeatRate(rate: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setKeyboardRepeatRate(rate: int, callback: AsyncCallback&lt;void&gt;): void

设置键盘按键的重复速率，使用Callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| rate    | ArkTS-Dyn: number <br> ArkTS-Sta: int| 是    | 键盘按键重复速率，默认值50ms/次，调节范围[36ms/次，100ms/次]。 |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Dyn示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setKeyboardRepeatRate(60, (error: Error) => {
              if (error) {
                console.error(`Set keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Set keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Set keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setKeyboardRepeatRate(60, (error:  BusinessError<void>|null, undefined) => {
              if (error) {
                console.error(`Set keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Set keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Set keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.setKeyboardRepeatRate<sup>10+</sup>

ArkTS-Dyn: setKeyboardRepeatRate(rate: number): Promise&lt;void&gt;

ArkTS-Sta: setKeyboardRepeatRate(rate: int): Promise&lt;void&gt;

设置键盘按键的重复速率，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| rate | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是    | 键盘按键重复速率，默认值50ms/次，调节范围[36ms/次，100ms/次]。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setKeyboardRepeatRate(60).then(() => {
              console.log(`Set keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Set keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatRate<sup>10+</sup>

ArkTS-Dyn: getKeyboardRepeatRate(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getKeyboardRepeatRate(callback: AsyncCallback&lt;int&gt;): void

获取键盘按键的重复速率，使用Callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;int&gt; | 是    | 回调函数，返回键盘按键的重复速率。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Dyn示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatRate((error: Error, rate: Number) => {
              if (error) {
                console.error(`Get keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Get keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatRate((error: BusinessError<void>|null, rate: int|undefined ) => {
              if (error) {
                console.error(`Get keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Get keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardRepeatRate<sup>10+</sup>

ArkTS-Dyn: getKeyboardRepeatRate(): Promise&lt;number&gt;

ArkTS-Sta: getKeyboardRepeatRate(): Promise&lt;int&gt;

获取键盘按键的重复速率，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回键盘按键的重复速率。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

ArkTS-Dyn示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatRate().then((rate: Number) => {
              console.log(`Get keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.getKeyboardRepeatRate().then((rate: int) => {
              console.log(`Get keyboard repeat rate success`);
            });
          } catch (error) {
            console.error(`Get keyboard repeat rate failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.setInputDeviceEnabled<sup>18+</sup>

ArkTS-Dyn: setInputDeviceEnabled(deviceId: number, enabled: boolean): Promise&lt;void&gt;

ArkTS-Sta: setInputDeviceEnabled(deviceId: int, enabled: boolean): Promise&lt;void&gt;

设置输入设备的开关状态。以触摸屏为例：关闭时，点击触摸屏设备不响应；开启时，可正常操作触摸屏。

**需要权限**：ohos.permission.INPUT_DEVICE_CONTROLLER

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**系统API**：此接口为系统接口。

**ArkTS-Dyn起始版本**：18

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名   | 类型    | 必填 | 说明                      |
| -------- | ------- | ---- | ------------------------- |
| deviceId | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 是   | 目标设备Id。              |
| enabled  | boolean | 是   | 输入设备的开关状态，取值为true表示开启输入设备，取值为false表示关闭输入设备。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[模块错误码](errorcode-inputdevice.md)。


| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | Not system application.                                      |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| 3900001  | The specified device does not exist.                         |

示例：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setInputDeviceEnabled(0, true).then(() => {
              console.info(`Set input device enable success`);
            });
          } catch (error) {
            console.error(`Set input device enable error`);
          }
        })
    }
  }
}
```
