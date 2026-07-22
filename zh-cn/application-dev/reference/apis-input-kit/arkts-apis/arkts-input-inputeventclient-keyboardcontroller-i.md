# KeyboardController

提供模拟按键操作的功能。模拟按键操作序列必须满足以下要求：

1. 按键只能在抬起状态下被按下，或者在该按键是最近按下的按键且未抬起的情况下被按下。2. 按键只能在被按下后才能抬起。3. 最多可以同时按下并保持五个按键。

**起始版本：** 26.0.0

<!--Device-inputEventClient-interface KeyboardController--><!--Device-inputEventClient-interface KeyboardController-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## pressKey

```TypeScript
pressKey(keyCode: KeyCode): Promise<void>
```

按下按键。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONTROL_DEVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyboardController-pressKey(keyCode: KeyCode): Promise<void>--><!--Device-KeyboardController-pressKey(keyCode: KeyCode): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyCode | [KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md) | 是 | 要按下的按键键码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-状态错误) | The key is already pressed and is not the most recently pressed key. |
| [3800001](../errorcode-infraredemitter.md#3800001-多模输入服务内部错误) | Input service exception. |

**示例：**

```TypeScript
import { inputEventClient, KeyCode } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createKeyboardController()
            .then((keyboardController: inputEventClient.KeyboardController) => {
              keyboardController.pressKey(KeyCode.KEYCODE_A);
              return keyboardController;
            })
            .then((keyboardController: inputEventClient.KeyboardController) => {
              keyboardController.releaseKey(KeyCode.KEYCODE_A);
            })
            .then(() => {
              console.info('Succeeded in releasing key');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to release key. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}

```

## releaseKey

```TypeScript
releaseKey(keyCode: KeyCode): Promise<void>
```

抬起按键。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONTROL_DEVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyboardController-releaseKey(keyCode: KeyCode): Promise<void>--><!--Device-KeyboardController-releaseKey(keyCode: KeyCode): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyCode | [KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md) | 是 | 要抬起的按键键码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [4300001](../errorcode-inputeventclient.md#4300001-状态错误) | The key is not pressed. |
| [3800001](../errorcode-infraredemitter.md#3800001-多模输入服务内部错误) | Input service exception. |

**示例：**

参见[pressKey](#presskey)示例。

