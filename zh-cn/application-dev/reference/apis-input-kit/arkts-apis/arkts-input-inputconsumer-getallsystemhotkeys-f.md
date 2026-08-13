# getAllSystemHotkeys

## getAllSystemHotkeys

```TypeScript
function getAllSystemHotkeys(): Promise<Array<HotkeyOptions>>
```

获取所有系统快捷键，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputConsumer-function getAllSystemHotkeys(): Promise<Array<HotkeyOptions>>--><!--Device-inputConsumer-function getAllSystemHotkeys(): Promise<Array<HotkeyOptions>>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md)&gt;&gt; | Promise对象，返回所有系统快捷键的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取所有系统热键
          inputConsumer.getAllSystemHotkeys().then((data: Array<inputConsumer.HotkeyOptions>) => {
            console.info(`Succeeded in getting list of system hotkeys: ${JSON.stringify(data)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get all system hotkeys, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取所有系统热键
          inputConsumer.getAllSystemHotkeys().then((data: Array<inputConsumer.HotkeyOptions>) => {
            console.info(`Succeeded in getting list of system hotkeys: ${JSON.stringify(data)}.`);
          }).catch((error) => {
            console.error(`Failed to get all system hotkeys, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}
```

