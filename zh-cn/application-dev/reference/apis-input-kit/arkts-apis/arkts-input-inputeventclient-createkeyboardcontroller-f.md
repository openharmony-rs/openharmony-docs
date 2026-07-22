# createKeyboardController

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## createKeyboardController

```TypeScript
function createKeyboardController(): Promise<KeyboardController>
```

创建键盘控制器，用于模拟按键操作。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONTROL_DEVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputEventClient-function createKeyboardController(): Promise<KeyboardController>--><!--Device-inputEventClient-function createKeyboardController(): Promise<KeyboardController>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KeyboardController&gt; | Promise对象，返回键盘控制器实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3800001](../errorcode-infraredemitter.md#3800001-多模输入服务内部错误) | Input service exception. |

**示例：**

```TypeScript
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputEventClient.createKeyboardController()
            .then(keyboardController => {
              console.info('Succeeded in creating keyboard controller');
            })
            .catch((error: BusinessError) => {
              console.error(`Failed to create keyboard controller. Code: ${error.code}, message: ${error.message}.`);
            });
        })
    }
  }
}

```

