# onHotkeyChange

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## onHotkeyChange

```TypeScript
function onHotkeyChange(hotkeyOptions: HotkeyOptions, callback: Callback<HotkeyOptions>): void
```

订阅应用快捷键。获取满足条件的组合按键输入事件，使用Callback异步回调。

**起始版本：** 23

<!--Device-inputConsumer-function onHotkeyChange(hotkeyOptions: HotkeyOptions, callback: Callback<HotkeyOptions>): void--><!--Device-inputConsumer-function onHotkeyChange(hotkeyOptions: HotkeyOptions, callback: Callback<HotkeyOptions>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hotkeyOptions | [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | 是 | 快捷键选项。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md)&gt; | 是 | 回调函数，获取满足条件的组合按键输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [4200002](../errorcode-inputconsumer.md#4200002-快捷键被系统注册) | The hotkey has been used by the system. |
| [4200003](../errorcode-inputconsumer.md#4200003-快捷键已经被其他应用注册) | The hotkey has been subscribed to by another. |

**示例**

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
          let leftCtrlKey = 2072;
          let zKey = 2042;
          let hotkeyOptions: inputConsumer.HotkeyOptions = {
            preKeys: [ leftCtrlKey ],
            finalKey: zKey,
            isRepeat: true
          };
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          }
          try {
            inputConsumer.onHotkeyChange(hotkeyOptions, hotkeyCallback);
          } catch (error) {
            console.error(`Failed to Subscribe hot key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

