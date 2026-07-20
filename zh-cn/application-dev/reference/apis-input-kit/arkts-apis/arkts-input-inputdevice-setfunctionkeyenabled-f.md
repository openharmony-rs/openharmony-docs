# setFunctionKeyEnabled

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

<a id="setfunctionkeyenabled"></a>
## setFunctionKeyEnabled

```TypeScript
function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise<void>
```

设置功能键（如：CapsLock键）使能状态。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.INPUT_KEYBOARD_CONTROLLER

<!--Device-inputDevice-function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise<void>--><!--Device-inputDevice-function setFunctionKeyEnabled(functionKey: FunctionKey, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| functionKey | [FunctionKey](arkts-input-inputdevice-functionkey-e.md) | 是 | 需要设置的功能键类型。 |
| enabled | boolean | 是 | 功能键使能状态。取值为true表示使能功能键，取值为false表示不使能功能键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [3900002](../errorcode-inputdevice.md#3900002-键盘设备没有连接) | There is currently no keyboard device connected. |
| [3900003](../errorcode-inputdevice.md#3900003-非输入法应用调用) | It is prohibited for non-input applications. |

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
            // 设置功能键使能状态
            inputDevice.setFunctionKeyEnabled(inputDevice.FunctionKey.CAPS_LOCK, true).then(() => {
              console.info(`Succeeded in setting capslock state.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set capslock state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          } catch (error) {
            console.error(`Failed to set capslock enable, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

