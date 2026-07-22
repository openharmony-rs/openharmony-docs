# isFunctionKeyEnabled

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## isFunctionKeyEnabled

```TypeScript
function isFunctionKeyEnabled(functionKey: FunctionKey): Promise<boolean>
```

检查功能键（如：CapsLock键）是否使能。使用Promise异步回调。

**起始版本：** 15

<!--Device-inputDevice-function isFunctionKeyEnabled(functionKey: FunctionKey): Promise<boolean>--><!--Device-inputDevice-function isFunctionKeyEnabled(functionKey: FunctionKey): Promise<boolean>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| functionKey | [FunctionKey](arkts-input-inputdevice-functionkey-e.md) | 是 | 需要设置的功能键类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回查询结果，true表示功能键使能，false表示功能键未使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [3900002](../errorcode-inputdevice.md#3900002-键盘设备没有连接) | There is currently no keyboard device connected. |

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
            // 查询功能键是否使能
            inputDevice.isFunctionKeyEnabled(inputDevice.FunctionKey.CAPS_LOCK).then((state: boolean) => {
              console.info(`Succeeded in getting capslock state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get capslock state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get capslock state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

