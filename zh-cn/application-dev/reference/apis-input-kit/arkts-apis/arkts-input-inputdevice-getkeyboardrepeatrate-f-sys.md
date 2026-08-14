# getKeyboardRepeatRate（系统接口）

## getKeyboardRepeatRate

```TypeScript
function getKeyboardRepeatRate(callback: AsyncCallback<int>): void
```

获取键盘按键的重复速率，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-function getKeyboardRepeatRate(callback: AsyncCallback<int>): void--><!--Device-inputDevice-function getKeyboardRepeatRate(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。当获取成功，err为undefined，data为键盘按键的重复速率；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

## 示例

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

ArkTS-Sta示例:

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
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
            inputDevice.getKeyboardRepeatRate((error: BusinessError<void>|null, rate: int|undefined ) => {
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


## getKeyboardRepeatRate

```TypeScript
function getKeyboardRepeatRate(): Promise<int>
```

获取键盘按键的重复速率，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-function getKeyboardRepeatRate(): Promise<int>--><!--Device-inputDevice-function getKeyboardRepeatRate(): Promise<int>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回键盘按键的重复速率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

## 示例

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
          try {
            // 获取键盘重复速率
            inputDevice.getKeyboardRepeatRate().then((rate: number) => {
              console.info(`Succeeded in getting keyboard repeat rate.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```TypeScript
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

