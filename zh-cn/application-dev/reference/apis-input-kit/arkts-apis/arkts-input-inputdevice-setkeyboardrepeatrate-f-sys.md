# setKeyboardRepeatRate（系统接口）

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## setKeyboardRepeatRate

```TypeScript
function setKeyboardRepeatRate(rate: number, callback: AsyncCallback<void>): void
```

设置键盘按键的重复速率，使用callback异步回调。

**起始版本：** 10

<!--Device-inputDevice-function setKeyboardRepeatRate(rate: int, callback: AsyncCallback<void>): void--><!--Device-inputDevice-function setKeyboardRepeatRate(rate: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | 键盘按键重复速率，默认值50ms/次，调节范围[36ms/次，100ms/次]。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置键盘按键重复速率成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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


## setKeyboardRepeatRate

```TypeScript
function setKeyboardRepeatRate(rate: number): Promise<void>
```

设置键盘按键的重复速率，使用Promise异步回调。

**起始版本：** 10

<!--Device-inputDevice-function setKeyboardRepeatRate(rate: int): Promise<void>--><!--Device-inputDevice-function setKeyboardRepeatRate(rate: int): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rate | number | 是 | 键盘按键重复速率，默认值50ms/次，调节范围[36ms/次，100ms/次]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
            // 按键重复速率60ms/次
            inputDevice.setKeyboardRepeatRate(60).then(() => {
              console.info(`Succeeded in setting keyboard repeat rate.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set keyboard repeat delay, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set keyboard repeat rate, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

