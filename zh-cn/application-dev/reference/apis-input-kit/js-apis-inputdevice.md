# @ohos.multimodalInput.inputDevice (输入设备)


本模块提供输入设备管理能力，包括监听输入设备的连接和断开状态，查询设备名称等输入设备信息。


> **说明**：
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块


```js
import { inputDevice } from '@kit.InputKit';
```

## inputDevice.getDeviceList<sup>9+</sup>

ArkTS-Dyn: getDeviceList(callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: getDeviceList(callback: AsyncCallback&lt;Array&lt;int&gt;&gt;): void

获取所有输入设备的id列表，使用Callback回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型                                     | 必填 | 说明                                     |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| callback |ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt; ArkTS-Sta:  AsyncCallback&lt;Array&lt;int&gt;&gt;| 是   | 回调函数，返回所有输入设备的id列表。id是输入设备的唯一标识。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**ArkTS-Dyn示例**：

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
            inputDevice.getDeviceList((error: Error, ids: Array<Number>) => {
              if (error) {
                console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Device id list: ${JSON.stringify(ids)}`);
            });
          } catch (error) {
            console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

**ArkTS-Sta示例**：

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
            inputDevice.getDeviceList((error: BusinessError<void>, ids: Array<int>) => {
              if (error) {
                console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Device id list: ${JSON.stringify(ids)}`);
            });
          } catch (error) {
            console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getDeviceList<sup>9+</sup>

ArkTS-Dyn: getDeviceList(): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: getDeviceList(): Promise&lt;Array&lt;int&gt;&gt;

获取所有输入设备的id列表，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**返回值**：

| 类型                               | 说明                                        |
| ---------------------------------- | ------------------------------------------- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt; <br>  ArkTS-Sta: Promise&lt;Array&lt;int&gt;&gt; | Promise对象，返回所有输入设备的id列表。 |

**ArkTS-Dyn示例**：

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
            inputDevice.getDeviceList().then((ids: Array<Number>) => {
              console.log(`Device id list: ${JSON.stringify(ids)}`);
            });
          } catch (error) {
            console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

**ArkTS-Sta示例**：

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
            inputDevice.getDeviceList().then((ids: Array<int>) => {
              console.log(`Device id list: ${JSON.stringify(ids)}`);
            });
          } catch (error) {
            console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getDeviceInfo<sup>9+</sup>

ArkTS-Dyn: getDeviceInfo(deviceId: number, callback: AsyncCallback&lt;InputDeviceData&gt;): void

ArkTS-Sta: getDeviceInfo(deviceId: int, callback: AsyncCallback&lt;InputDeviceData&gt;): void

获取指定输入设备的信息，使用Callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型                                                     | 必填 | 说明                                    |
| -------- | -------------------------------------------------------- | ---- | --------------------------------------- |
| deviceId | ArkTS-Dyn: number<br> ArkTS-Sta: int                                                 | 是   | 输入设备id。                  |
| callback | AsyncCallback&lt;[InputDeviceData](#inputdevicedata)&gt; | 是   | 回调函数。返回输入设备信息，包括输入设备id、名称、支持的输入能力、物理地址、版本信息及产品信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**ArkTS-Dyn示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取输入设备id为1的设备信息。
          try {
            inputDevice.getDeviceInfo(1, (error: Error, deviceData: inputDevice.InputDeviceData) => {
              if (error) {
                console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Device info: ${JSON.stringify(deviceData)}`);
            });
          } catch (error) {
            console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

**ArkTS-Sta示例**：

```ts
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取输入设备id为1的设备信息。
          try {
            inputDevice.getDeviceInfo(1, (error: BusinessError<void>|null, deviceData: inputDevice.InputDeviceData | undefined) => {
              if (error) {
                console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Device info: ${JSON.stringify(deviceData)}`);
            });
          } catch (error) {
            console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getDeviceInfo<sup>9+</sup>

ArkTS-Dyn: getDeviceInfo(deviceId: number): Promise&lt;InputDeviceData&gt;

ArkTS-Sta: getDeviceInfo(deviceId: int): Promise&lt;InputDeviceData&gt;

获取指定id的输入设备信息，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                   |
| -------- | ------ | ---- | ---------------------- |
| deviceId | ArkTS-Dyn: number <br> ArkTS-Dyn: int | 是   | 输入设备id。 |

**返回值**：

| 类型                                               | 说明                            |
| -------------------------------------------------- | ------------------------------- |
| Promise&lt;[InputDeviceData](#inputdevicedata)&gt; | Promise对象，返回输入设备信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取输入设备id为1的设备信息。
          try {
            inputDevice.getDeviceInfo(1).then((deviceData: inputDevice.InputDeviceData) => {
              console.log(`Device info: ${JSON.stringify(deviceData)}`);
            });
          } catch (error) {
            console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getDeviceInfoSync<sup>10+</sup>

ArkTS-Dyn: getDeviceInfoSync(deviceId: number): InputDeviceData

ArkTS-Sta: getDeviceInfoSync(deviceId: int): InputDeviceData

获取指定输入设备的信息。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                   |
| -------- | ------ | ---- | ---------------------- |
| deviceId | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 是   | 输入设备id。 |

**返回值**：

| 类型                                               | 说明                            |
| -------------------------------------------------- | ------------------------------- |
| [InputDeviceData](#inputdevicedata) | 返回输入设备信息，包括输入设备id、名称、支持的源类型、物理地址、版本信息及产品信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取输入设备id为1的设备信息。
          try {
            let deviceData: inputDevice.InputDeviceData = inputDevice.getDeviceInfoSync(1);
            console.log(`Device info: ${JSON.stringify(deviceData)}`);
          } catch (error) {
            console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id="on_change">inputDevice.on<sup>9+</sup></span>

on(type: "change", listener: Callback&lt;DeviceListener&gt;): void

注册监听输入设备的热插拔事件，使用时需连接鼠标、键盘、触摸屏等外部设备。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[onChange](#onChange)

**ArkTS-Dyn起始版本**：9

**参数**：

| 参数名       | 类型                                       | 必填   | 说明          |
| -------- | ---------------------------------------- | ---- | ----------- |
| type     | string                                   | 是    | 输入设备的事件类型，固定值为'change'。  |
| listener | Callback&lt;[DeviceListener](#devicelistener9)&gt; | 是    | 回调函数，异步上报输入设备热插拔事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let isPhysicalKeyboardExist = true;
          try {
            inputDevice.on("change", (data: inputDevice.DeviceListener) => {
              console.log(`Device event info: ${JSON.stringify(data)}`);
              inputDevice.getKeyboardType(data.deviceId, (err: Error, type: inputDevice.KeyboardType) => {
                console.log("The keyboard type is: " + type);
                if (type == inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type == 'add') {
                  // 监听物理键盘已连接。
                  isPhysicalKeyboardExist = true;
                } else if (type == inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type == 'remove') {
                  // 监听物理键盘已断开。
                  isPhysicalKeyboardExist = false;
                }
              });
            });
            // 根据isPhysicalKeyboardExist的值决定软键盘是否弹出。
          } catch (error) {
            console.error(`Get device info failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id="onChange">inputDevice.onChange<sup>22+</sup></span>

onChange(listener: Callback&lt;DeviceListener&gt;): void

注册监听输入设备的热插拔事件，使用时需连接鼠标、键盘、触摸屏等外部设备。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[on](#on_change)

**ArkTS-Dyn起始版本**：22

**参数**：

| 参数名       | 类型                                       | 必填   | 说明          |
| -------- | ---------------------------------------- | ---- | ----------- |
| listener | Callback&lt;[DeviceListener](#devicelistener9)&gt; | 是    | 回调函数，异步上报输入设备热插拔事件。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```ts
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let isPhysicalKeyboardExist = true;
          try {
            inputDevice.onChange((data: inputDevice.DeviceListener) => {
              console.log(`Device event info: ${JSON.stringify(data)}`);
              inputDevice.getKeyboardType(data.deviceId, (err: Error, type: inputDevice.KeyboardType) => {
                console.log("The keyboard type is: " + type);
                if (type == inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type == 'add') {
                  // 监听物理键盘已连接。
                  isPhysicalKeyboardExist = true;
                } else if (type == inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type == 'remove') {
                  // 监听物理键盘已断开。
                  isPhysicalKeyboardExist = false;
                }
              });
            });
            // 根据isPhysicalKeyboardExist的值决定软键盘是否弹出。
          } catch (error) {
            console.error(`Get device info failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "off_change">inputDevice.off<sup>9+</sup></span>

off(type: "change", listener?: Callback&lt;DeviceListener&gt;): void

取消监听输入设备的热插拔事件。在应用退出前调用，取消监听。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS模式**: 该接口仅适用于ArkTS-Dyn。

**相关接口**: 该接口对应的ArkTS-Sta接口是[offChange](#offChange22)

**ArkTS-Dyn起始版本**：9

**参数**：

| 参数名       | 类型                                       | 必填   | 说明          |
| -------- | ---------------------------------------- | ---- | ----------- |
| type     | string                                   | 是    | 输入设备的事件类型，固定值为'change'。  |
| listener | Callback&lt;[DeviceListener](#devicelistener9)&gt; | 否    | 取消监听的回调函数，缺省时取消所有输入设备热插拔事件的监听。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let callback = (data: inputDevice.DeviceListener) => {
            console.log(`Report device event info: ${JSON.stringify(data, [`type`, `deviceId`])}`);
          };

          try {
            inputDevice.on("change", callback);
          } catch (error) {
            console.error(`Listen device event failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }

          // 取消指定的监听。
          try {
            inputDevice.off("change", callback);
          } catch (error) {
            console.error(`Cancel listening device event failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }

          // 取消所有监听。
          try {
            inputDevice.off("change");
          } catch (error) {
            console.error(`Cancel all listening device event failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## <span id = "offChange22">inputDevice.off<sup>22+</sup></span>

off(type: "change", listener?: Callback&lt;DeviceListener&gt;): void

取消监听输入设备的热插拔事件。在应用退出前调用，取消监听。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS模式**: 该接口仅适用于ArkTS-Sta。

**相关接口**: 该接口对应的ArkTS-Dyn接口是[off](#off_Change)

**ArkTS-Dyn起始版本**：22

**参数**：

| 参数名       | 类型                                       | 必填   | 说明          |
| -------- | ---------------------------------------- | ---- | ----------- |
| listener | Callback&lt;[DeviceListener](#devicelistener9)&gt; | 否    | 取消监听的回调函数，缺省时取消所有输入设备热插拔事件的监听。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let callback = (data: inputDevice.DeviceListener) => {
            console.log(`Report device event info: ${JSON.stringify(data, [`type`, `deviceId`])}`);
          };

          try {
            inputDevice.onChange(callback);
          } catch (error) {
            console.error(`Listen device event failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }

          // 取消指定的监听。
          try {
            inputDevice.offChange(callback);
          } catch (error) {
            console.error(`Cancel listening device event failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }

          // 取消所有监听。
          try {
            inputDevice.offChange();
          } catch (error) {
            console.error(`Cancel all listening device event failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getDeviceIds<sup>(deprecated)</sup>

getDeviceIds(callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

获取所有输入设备的id列表，使用Callback异步回调。

> 从API version 9 开始不再维护，建议使用[inputDevice.getDeviceList](#inputdevicegetdevicelist9)代替。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**参数**：

| 参数名     | 类型                                     | 必填 | 说明                                     |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| callback | AsyncCallback&lt;Array&lt;number&gt;&gt; | 是   | 回调函数，返回输入设备的id列表。 |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputDevice.getDeviceIds((error: Error, ids: Array<Number>) => {
            if (error) {
              console.error(`Failed to get device id list, error: ${JSON.stringify(error, [`code`, `message`])}`);
              return;
            }
            console.log(`Device id list: ${JSON.stringify(ids)}`);
          });
        })
    }
  }
}
```

## inputDevice.getDeviceIds<sup>(deprecated)</sup>

getDeviceIds(): Promise&lt;Array&lt;number&gt;&gt;

获取所有输入设备的id列表，使用Promise异步回调。

> 从API version 9 开始不再维护，建议使用[inputDevice.getDeviceList](#inputdevicegetdevicelist9)代替。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**返回值**：

| 类型                               | 说明                                        |
| ---------------------------------- | ------------------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise对象，返回所有输入设备的id列表。 |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputDevice.getDeviceIds().then((ids: Array<Number>) => {
            console.log(`Device id list: ${JSON.stringify(ids)}`);
          });
        })
    }
  }
}
```

## inputDevice.getDevice<sup>(deprecated)</sup>

getDevice(deviceId: number, callback: AsyncCallback&lt;InputDeviceData&gt;): void

获取指定id的输入设备信息，使用Callback异步回调。

> 从API version 9 开始不再维护，建议使用[inputDevice.getDeviceInfo](#inputdevicegetdeviceinfo9)代替。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**参数**：

| 参数名     | 类型                                                     | 必填 | 说明                             |
| -------- | -------------------------------------------------------- | ---- | -------------------------------- |
| deviceId | number                                                   | 是   | 输入设备id。                     |
| callback | AsyncCallback&lt;[InputDeviceData](#inputdevicedata)&gt; | 是   | 回调函数，返回输入设备信息。 |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取输入设备id为1的设备信息。
          inputDevice.getDevice(1, (error: Error, deviceData: inputDevice.InputDeviceData) => {
            if (error) {
              console.error(`Failed to get device info, error: ${JSON.stringify(error, [`code`, `message`])}`);
              return;
            }
            console.log(`Device info: ${JSON.stringify(deviceData)}`);
          });
        })
    }
  }
}
```

## inputDevice.getDevice<sup>(deprecated)</sup>

getDevice(deviceId: number): Promise&lt;InputDeviceData&gt;

获取指定id的输入设备信息，使用Promise异步回调。

> 从API version 9 开始不再维护，建议使用[inputDevice.getDeviceInfo](#inputdevicegetdeviceinfo9)代替。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**参数**：

| 参数名     | 类型   | 必填 | 说明         |
| -------- | ------ | ---- | ------------ |
| deviceId | number | 是   | 输入设备id。 |

**返回值**：

| 类型                                               | 说明                                |
| -------------------------------------------------- | ----------------------------------- |
| Promise&lt;[InputDeviceData](#inputdevicedata)&gt; | Promise对象，返回输入设备信息。 |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取输入设备id为1的设备信息。
          inputDevice.getDevice(1).then((deviceData: inputDevice.InputDeviceData) => {
            console.log(`Device info: ${JSON.stringify(deviceData)}`);
          });
        })
    }
  }
}
```

## inputDevice.supportKeys<sup>9+</sup>

ArkTS-Dyn: supportKeys(deviceId: number, keys: Array&lt;KeyCode&gt;, callback: AsyncCallback &lt;Array&lt;boolean&gt;&gt;): void

ArkTS-Sta: supportKeys(deviceId: int, keys: Array&lt;KeyCode&gt;, callback: AsyncCallback &lt;Array&lt;boolean&gt;&gt;): void


查询指定输入设备是否支持指定按键，使用Callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型                                      | 必填 | 说明                                                   |
| -------- | ----------------------------------------- | ---- | ------------------------------------------------------ |
| deviceId | ArkTS-Dyn: number <br> ArkTS-Sta: int  | 是   | 输入设备的id。对于同一个物理设备，反复插拔会导致设备id发生变化。 |
| keys     | Array[&lt;KeyCode&gt;](js-apis-keycode.md#keycode)  | 是   | 需要查询的键码值，最多支持5个按键查询。                |
| callback | AsyncCallback&lt;Array&lt;boolean&gt;&gt; | 是   | 回调函数，返回查询结果。                           |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**ArkTS-Dyn示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询id为1的输入设备对于17、22和2055按键的支持情况。
          try {
            inputDevice.supportKeys(1, [17, 22, 2055], (error: Error, supportResult: Array<Boolean>) => {
              console.log(`Query result: ${JSON.stringify(supportResult)}`);
            });
          } catch (error) {
            console.error(`Query failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

**ArkTS-Dyn示例**：

```ts
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询id为1的输入设备对于17、22和2055按键的支持情况。
          try {
            inputDevice.supportKeys(1, [17, 22, 2055], (error: BusinessError | null, supportResult: Array<Boolean> | undefined) => {
              console.log(`Query result: ${JSON.stringify(supportResult)}`);
            });
          } catch (error) {
            console.error(`Query failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.supportKeys<sup>9+</sup>

ArkTS-Dyn: supportKeys(deviceId: number, keys: Array&lt;KeyCode&gt;): Promise&lt;Array&lt;boolean&gt;&gt;

ArkTS-Sta: supportKeys(deviceId: number, keys: Array&lt;KeyCode&gt;): Promise&lt;Array&lt;boolean&gt;&gt;

查询指定输入设备是否支持指定按键，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型                 | 必填 | 说明                                                   |
| -------- | -------------------- | ---- | ------------------------------------------------------ |
| deviceId | ArkTS-Dyn: number <br> ArkTS-Sta: int              | 是   | 输入设备的id。对于同一个物理设备，反复插拔会导致设备id发生变化。 |
| keys     | Array[&lt;KeyCode&gt;](js-apis-keycode.md#keycode) | 是   | 需要查询的键码值，最多支持查询5个按键。                |

**返回值**：

| 类型                                | 说明                            |
| ----------------------------------- | ------------------------------- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise对象，返回查询结果。true 表示支持，false表示不支持。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询id为1的输入设备对于17、22和2055按键的支持情况。
          try {
            inputDevice.supportKeys(1, [17, 22, 2055]).then((supportResult: Array<Boolean>) => {
              console.log(`Query result: ${JSON.stringify(supportResult)}`);
            });
          } catch (error) {
            console.error(`Query failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.supportKeysSync<sup>10+</sup>

ArkTS-Dyn: supportKeysSync(deviceId: number, keys: Array&lt;KeyCode&gt;): Array&lt;boolean&gt;

ArkTS-Sta: supportKeysSync(deviceId: int, keys: Array&lt;KeyCode&gt;): Array&lt;boolean&gt;

查询指定id的输入设备对指定键码值的支持情况。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型                 | 必填 | 说明                                                   |
| -------- | -------------------- | ---- | ------------------------------------------------------ |
| deviceId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 输入设备的id。对于同一个物理设备，反复插拔会导致设备id发生变化。 |
| keys     | Array[&lt;KeyCode&gt;](js-apis-keycode.md#keycode) | 是   | 需要查询的键码值，最多支持查询5个按键。                |

**返回值**：

| 类型                                | 说明                            |
| ----------------------------------- | ------------------------------- |
| Array&lt;boolean&gt; | 返回查询结果。true表示支持，false表示不支持。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询id为1的输入设备对于17、22和2055按键的支持情况。
          try {
            let supportResult: Array<Boolean> = inputDevice.supportKeysSync(1, [17, 22, 2055])
            console.log(`Query result: ${JSON.stringify(supportResult)}`)
          } catch (error) {
            console.error(`Query failed, error: ${JSON.stringify(error, [`code`, `message`])}`)
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardType<sup>9+</sup>

ArkTS-Dyn: getKeyboardType(deviceId: number, callback: AsyncCallback&lt;KeyboardType&gt;): void

ArkTS-Sta: getKeyboardType(deviceId: int, callback: AsyncCallback&lt;KeyboardType&gt;): void

获取输入设备的键盘类型，如全键盘、小键盘等，使用callback异步回调。输入设备的键盘类型以接口返回结果为准。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型                                                | 必填 | 说明                                                         |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| deviceId | ArkTS-Dyn: number <br> ArkTS-Sta: int        | 是   | 输入设备的唯一标识，同一个物理设备反复插拔，设备id会发生变化。 |
| callback | AsyncCallback&lt;[KeyboardType](#keyboardtype9)&gt; | 是   | 回调函数，返回查询结果。                                 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**ArkTS-Dyn示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询id为1的输入设备的键盘类型。
          try {
            inputDevice.getKeyboardType(1, (error: Error, type: Number) => {
              if (error) {
                console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Keyboard type: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

**ArkTS-Sta示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询id为1的输入设备的键盘类型。
          try {
            inputDevice.getKeyboardType(1, (error: BusinessError | null, type: int | undefined) => {
              if (error) {
                console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.log(`Keyboard type: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardType<sup>9+</sup>

ArkTS-Dyn: getKeyboardType(deviceId: number): Promise&lt;KeyboardType&gt;

ArkTS-Sta: getKeyboardType(deviceId: int): Promise&lt;KeyboardType&gt;

获取输入设备的键盘类型，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名    | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| deviceId | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是   | 输入设备的唯一标识，同一个物理设备反复插拔，设备id会发生变化。 |

**返回值**：

| 类型                                          | 说明                            |
| --------------------------------------------- | ------------------------------- |
| Promise&lt;[KeyboardType](#keyboardtype9)&gt; | Promise对象，返回查询结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**ArkTS-Dyn示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 示例查询设备id为1的设备键盘类型。
          try {
            inputDevice.getKeyboardType(1).then((type: Number) => {
              console.log(`Keyboard type: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```
**ArkTS-Sta示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 示例查询设备id为1的设备键盘类型。
          try {
            inputDevice.getKeyboardType(1).then((type: int) => {
              console.log(`Keyboard type: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.getKeyboardTypeSync<sup>10+</sup>

ArkTS-Dyn: getKeyboardTypeSync(deviceId: number): KeyboardType

ArkTS-Sta: getKeyboardTypeSync(deviceId: int): KeyboardType

获取输入设备的键盘类型。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| deviceId | ArkTS-Dyn: number <br> ArkTS-Sta: int| 是   | 输入设备的唯一标识，同一个物理设备反复插拔，设备id会发生变化。 |

**返回值**：

| 类型                                          | 说明                            |
| --------------------------------------------- | ------------------------------- |
| [KeyboardType](#keyboardtype9) | 返回查询结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**ArkTS-Dyn示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 示例查询设备id为1的设备键盘类型。
          try {
            let type: number = inputDevice.getKeyboardTypeSync(1)
            console.log(`Keyboard type: ${JSON.stringify(type)}`)
          } catch (error) {
            console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`)
          }
        })
    }
  }
}
```

**ArkTS-Sta示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 示例查询设备id为1的设备键盘类型。
          try {
            let type: int = inputDevice.getKeyboardTypeSync(1)
            console.log(`Keyboard type: ${JSON.stringify(type)}`)
          } catch (error) {
            console.error(`Failed to get keyboard type, error: ${JSON.stringify(error, [`code`, `message`])}`)
          }
        })
    }
  }
}
```

## inputDevice.isFunctionKeyEnabled<sup>15+</sup>

isFunctionKeyEnabled(functionKey: FunctionKey): Promise&lt;boolean&gt;

检查功能键（如：CapsLock键）是否使能。使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名     | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| functionKey | [FunctionKey](#functionkey15) | 是   | 需要设置的功能键类型。 |

**返回值**：

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回查询结果，true表示功能键使能，false表示功能键未使能。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[输入设备错误码](errorcode-inputdevice.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| 3900002      | There is currently no keyboard device connected. |

**示例**：

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
            inputDevice.isFunctionKeyEnabled(inputDevice.FunctionKey.CAPS_LOCK).then((state: boolean) => {
              console.log(`capslock state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`Failed to get capslock state, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputDevice.setFunctionKeyEnabled<sup>15+</sup>

setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise&lt;void&gt;

设置功能键（如：CapsLock键）使能状态。使用Promise异步回调。

**需要权限**：ohos.permission.INPUT_KEYBOARD_CONTROLLER

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：22

**参数**：

| 参数名   | 类型    | 必填 | 说明                      |
| -------- | ------- | ---- | ------------------------- |
| functionKey | [FunctionKey](#functionkey15) | 是   | 需要设置的功能键类型。 |
| enabled  | boolean | 是   | 功能键使能状态。取值为true表示使能功能键，取值为false表示不使能功能键。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[输入设备错误码](errorcode-inputdevice.md)。


| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| 3900002      | There is currently no keyboard device connected. |
| 3900003      | It is prohibited for non-input applications. |

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
            inputDevice.setFunctionKeyEnabled(inputDevice.FunctionKey.CAPS_LOCK, true).then(() => {
              console.info(`Set capslock state success`);
            }).catch((error: BusinessError) => {
              console.error(`Set capslock state failed, error=${JSON.stringify(error)}`);
            });
          } catch (error) {
            console.error(`Set capslock enable error`);
          }
        })
    }
  }
}
```

## inputDevice.getIntervalSinceLastInput<sup>14+</sup>

ArkTS-Dyn: getIntervalSinceLastInput(): Promise&lt;number&gt;

ArkTS-Sta: getIntervalSinceLastInput(): Promise&lt;long&gt;

获取距离上次系统输入事件的时间间隔（包含设备休眠时间），使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：22

**返回值**：

| 参数                                          | 说明                            |
| --------------------------------------------- | ------------------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br> ArkTS-Sta: Promise&lt;long&gt; | Promise对象，返回距离上次系统输入事件的时间间隔，单位为微秒（μs）。|

**ArkTS-Dyn示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputDevice.getIntervalSinceLastInput().then((timeInterval: number) => {
            console.log(`Interval since last input: ${JSON.stringify(timeInterval)}`);
          });
        })
    }
  }
}
```

**ArkTS-Sta示例**：

```js
import { inputDevice } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputDevice.getIntervalSinceLastInput().then((timeInterval: long) => {
            console.log(`Interval since last input: ${JSON.stringify(timeInterval)}`);
          });
        })
    }
  }
}
```

## DeviceListener<sup>9+</sup>

描述输入设备热插拔的信息。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称        | 类型   | 只读   | 可选   | 说明      |
| --------- | ------ | ---- | ---- | ------- |
| type     | [ChangedType](#changedtype9)| 否 | 否 | 输入设备插入或者移除。|
| deviceId | ArkTS-Dyn: number <br>ArkTS-Dyn: int     | 否 | 否 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备id会发生变化。 |

## InputDeviceData

描述输入设备的信息。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：22

| 名称        | 类型   | 只读   | 可选   | 说明      |
| --------- | ------ | ---- | ---- | ------- |
| id                   | ArkTS-Dyn: number <br>ArkTS-Dyn: int                                 | 否 | 否 | 输入设备的唯一标识，同一个物理设备反复插拔，设备id会发生变化。 |
| name                 | string                                 | 否 | 否 | 输入设备的名称。                                             |
| sources              | Array&lt;[SourceType](#sourcetype9)&gt; | 否 | 否 | 输入设备支持的输入能力。一个输入设备可以同时具备多种输入能力，如有的键盘上附带触摸板，则此设备有键盘和触摸板两种输入能力。 |
| axisRanges           | Array&lt;[AxisRange](#axisrange)&gt;  | 否 | 否 | 输入设备的轴信息。                                           |
| bus<sup>9+</sup>     | ArkTS-Dyn: number <br>ArkTS-Dyn: int | 否 | 否 | 输入设备的总线类型，该值以输入设备上报为准。      |
| product<sup>9+</sup> | ArkTS-Dyn: number <br>ArkTS-Dyn: int | 否 | 否 | 输入设备的产品信息。                                         |
| vendor<sup>9+</sup>  | ArkTS-Dyn: number <br>ArkTS-Dyn: int| 否 | 否 | 输入设备的厂商信息。                                         |
| version<sup>9+</sup> | ArkTS-Dyn: number <br>ArkTS-Dyn: int | 否 | 否 | 输入设备的版本信息。                                         |
| phys<sup>9+</sup>    | string                                 | 否 | 否 | 输入设备的物理地址。                                         |
| uniq<sup>9+</sup>    | string                                 | 否 | 否 | 输入设备的唯一标识。                                         |

## AxisType<sup>9+</sup>

type AxisType = 'touchmajor' | 'touchminor' | 'orientation' | 'x' | 'y' | 'pressure' | 'toolminor' | 'toolmajor' | 'null'

输入设备的轴类型。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 类型      |说明      |
| --------- | ------- |
| 'touchmajor'  | 椭圆触摸区域长轴。 |
| 'touchminor'  | 椭圆触摸区域短轴。 |
| 'toolminor'   | 工具区域短轴。 |
| 'toolmajor'   | 工具区域长轴。 |
| 'orientation' | 方向轴。 |
|'pressure'    | 压力轴。  |
| 'x'          | 横坐标轴。         |
| 'y'           | 纵坐标轴。         |
|'null'        |  无。             |

## AxisRange

输入设备的轴信息。

**系统能力**： SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：8

**ArkTS-Sta起始版本**：22

| 名称        | 类型   | 只读   | 可选   | 说明      |
| --------- | ------ | ---- | ---- | ------- |
| source                  | [SourceType](#sourcetype9) | 否 | 否 | 轴的输入能力。 |
| axis                    | [AxisType](#axistype9)    | 否 | 否 | 轴的类型。    |
| max                     | ArkTS-Dyn: number <br>ArkTS-Dyn: int| 否 | 否 | 轴的最大值。   |
| min                     | ArkTS-Dyn: number <br>ArkTS-Dyn: int| 否 | 否 | 轴的最小值。   |
| fuzz<sup>9+</sup>       | ArkTS-Dyn: number <br>ArkTS-Dyn: int| 否 | 否 | 轴的模糊值。   |
| flat<sup>9+</sup>       | ArkTS-Dyn: number <br>ArkTS-Dyn: int| 否 | 否 | 轴的基准值。   |
| resolution<sup>9+</sup> | ArkTS-Dyn: number <br>ArkTS-Dyn: int| 否 | 否 | 轴的分辨率。   |

## SourceType<sup>9+</sup>

type SourceType = 'keyboard' | 'mouse' | 'touchpad' | 'touchscreen' | 'joystick' | 'trackball'

轴的输入能力。比如鼠标设备可上报x轴事件，则x轴的输入源就是鼠标。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 类型       |说明      |
| --------- |  ------- |
| 'keyboard'    | 表示输入设备是键盘。  |
| 'touchscreen' | 表示输入设备是触摸屏。 |
| 'mouse'       | 表示输入设备是鼠标。  |
| 'trackball'   | 表示输入设备是轨迹球。 |
| 'touchpad'    | 表示输入设备是触摸板。 |
| 'joystick'   | 表示输入设备是操纵杆。 |

## ChangedType<sup>9+</sup>

type ChangedType = 'add' | 'remove'

监听设备热插拔事件类型。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 类型        | 说明      |
| --------- | ------- |
| 'add'    | 插入输入设备。 |
| 'remove' | 移除输入设备。 |

## KeyboardType<sup>9+</sup>

键盘输入设备的类型。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称                  | 值    | 说明        |
| ------------------- | ---- | --------- |
| NONE                | 0    | 表示无按键设备。  |
| UNKNOWN             | 1    | 表示未知按键设备。 |
| ALPHABETIC_KEYBOARD | 2    | 表示全键盘设备。  |
| DIGITAL_KEYBOARD    | 3    | 表示小键盘设备。  |
| HANDWRITING_PEN     | 4    | 表示手写笔设备。  |
| REMOTE_CONTROL      | 5    | 表示遥控器设备。  |

## FunctionKey<sup>15+</sup>

功能键的类型。

**系统能力**：SystemCapability.MultimodalInput.Input.InputDevice

**ArkTS-Dyn起始版本**：15

**ArkTS-Sta起始版本**：22

| 名称                  | 值    | 说明        |
| ------------------- | ---- | --------- |
| CAPS_LOCK                | 1    | CapsLock键，仅支持对输入键盘扩展的CapsLock键设置使能。 |