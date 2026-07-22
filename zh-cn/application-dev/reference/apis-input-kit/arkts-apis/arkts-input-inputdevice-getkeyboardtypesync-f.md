# getKeyboardTypeSync

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## getKeyboardTypeSync

```TypeScript
function getKeyboardTypeSync(deviceId: number): KeyboardType
```

获取输入设备的键盘类型。

**起始版本：** 10

<!--Device-inputDevice-function getKeyboardTypeSync(deviceId: int): KeyboardType--><!--Device-inputDevice-function getKeyboardTypeSync(deviceId: int): KeyboardType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyboardType](arkts-input-inputdevice-keyboardtype-e.md) | 返回查询结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

