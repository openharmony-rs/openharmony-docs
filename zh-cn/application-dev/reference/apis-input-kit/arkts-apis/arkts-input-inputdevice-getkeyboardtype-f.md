# getKeyboardType

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { inputDeviceCooperate } from '@kit.InputKit';
```

## getKeyboardType

```TypeScript
function getKeyboardType(deviceId: int, callback: AsyncCallback<KeyboardType>): void
```

获取输入设备的键盘类型，如全键盘、小键盘等。输入设备的键盘类型以接口返回结果为准。使用callback异步回调。

**起始版本：** 23

<!--Device-inputDevice-function getKeyboardType(deviceId: int, callback: AsyncCallback<KeyboardType>): void--><!--Device-inputDevice-function getKeyboardType(deviceId: int, callback: AsyncCallback<KeyboardType>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[KeyboardType](arkts-input-inputdevice-keyboardtype-e.md)&gt; | 是 | 回调函数。当查询成功，err为undefined，data为输入设备的键盘类型；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

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
          // 查询ID为1的输入设备的键盘类型。
          try {
            // 获取键盘类型
            inputDevice.getKeyboardType(1, (error: BusinessError, type: inputDevice.KeyboardType) => {
              if (error) {
                console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting keyboard type: ${JSON.stringify(type)}.`);
            });
          } catch (error) {
            console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { inputDevice } from '@kit.InputKit';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询ID为1的输入设备的键盘类型。
          try {
            // 获取键盘类型
            let tempType: int = 1;
            let funCallback: AsyncCallback<inputDevice.KeyboardType> = (error: BusinessError<void> | null, type: inputDevice.KeyboardType | undefined) => {
              if (error) {
                console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting keyboard type: ${JSON.stringify(type)}.`);
            }
            inputDevice.getKeyboardType(tempType, funCallback);
          } catch (error) {
            console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## getKeyboardType

```TypeScript
function getKeyboardType(deviceId: int): Promise<KeyboardType>
```

获取输入设备的键盘类型，使用Promise异步回调。

**起始版本：** 23

<!--Device-inputDevice-function getKeyboardType(deviceId: int): Promise<KeyboardType>--><!--Device-inputDevice-function getKeyboardType(deviceId: int): Promise<KeyboardType>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[KeyboardType](arkts-input-inputdevice-keyboardtype-e.md)&gt; | Promise对象，返回输入设备的键盘类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

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
          // 示例查询设备ID为1的设备键盘类型。
          try {
            // 获取键盘类型
            inputDevice.getKeyboardType(1).then((type: inputDevice.KeyboardType) => {
              console.info(`Succeeded in getting keyboard type: ${JSON.stringify(type)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { inputDevice } from '@kit.InputKit';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 示例查询设备ID为1的设备键盘类型。
          try {
            // 获取键盘类型
            let id: int = 1;
            let fun = (type: inputDevice.KeyboardType) => {
              console.info(`Succeeded in getting keyboard type: ${JSON.stringify(type)}.`);
            };
            inputDevice.getKeyboardType(id).then(fun);
          } catch (error) {
            console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

