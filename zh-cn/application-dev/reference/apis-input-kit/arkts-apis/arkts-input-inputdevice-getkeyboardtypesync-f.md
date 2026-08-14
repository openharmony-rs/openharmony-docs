# getKeyboardTypeSync

## getKeyboardTypeSync

```TypeScript
function getKeyboardTypeSync(deviceId: int): KeyboardType
```

获取输入设备的键盘类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-function getKeyboardTypeSync(deviceId: int): KeyboardType--><!--Device-inputDevice-function getKeyboardTypeSync(deviceId: int): KeyboardType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyboardType](arkts-input-inputdevice-keyboardtype-e.md) | 返回查询结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

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
          // 示例查询设备ID为1的设备键盘类型。
          try {
            let type: inputDevice.KeyboardType = inputDevice.getKeyboardTypeSync(1);
            console.info(`Succeeded in getting keyboard type: ${JSON.stringify(type)}.`);
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
            let type: int = inputDevice.getKeyboardTypeSync(1)
            console.info(`Succeeded in getting keyboard type: ${JSON.stringify(type)}.`)
          } catch (error) {
            console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`)
          }
        })
    }
  }
}
```

