# supportKeysSync

## supportKeysSync

```TypeScript
function supportKeysSync(deviceId: int, keys: Array<KeyCode>): Array<boolean>
```

查询指定id的输入设备对指定键值的支持情况。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-function supportKeysSync(deviceId: int, keys: Array<KeyCode>): Array<boolean>--><!--Device-inputDevice-function supportKeysSync(deviceId: int, keys: Array<KeyCode>): Array<boolean>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |
| keys | Array&lt;[KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)&gt; | 是 | 需要查询的键值，最多支持查询5个按键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;boolean&gt; | 返回查询结果。true表示支持，false表示不支持。 |

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
          // 查询ID为1的输入设备对于17、22和2055按键的支持情况。
          try {
            let supportResult: Array<Boolean> = inputDevice.supportKeysSync(1, [17, 22, 2055]);
            console.info(`Succeeded in querying support keys, result: ${JSON.stringify(supportResult)}.`);
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { inputDevice, KeyCode } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询ID为1的输入设备对于17、22和2055按键的支持情况。
          try {
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_DOWN, KeyCode.KEYCODE_VOLUME_MUTE, KeyCode.KEYCODE_DEL];
            let supportResult: Array<Boolean> = inputDevice.supportKeysSync(1, keys);
            console.info(`Succeeded in querying support keys, result: ${JSON.stringify(supportResult)}.`)
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`)
          }
        })
    }
  }
}
```

