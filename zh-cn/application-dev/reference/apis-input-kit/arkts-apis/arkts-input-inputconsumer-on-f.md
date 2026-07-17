# on

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## on('hotkeyChange')

```TypeScript
function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback<HotkeyOptions>): void
```

订阅应用快捷键。获取满足条件的组合按键输入事件，使用callback异步回调。

**起始版本：** 14

<!--Device-inputConsumer-function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback<HotkeyOptions>): void--><!--Device-inputConsumer-function on(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback: Callback<HotkeyOptions>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotkeyChange' | 是 | 事件类型，固定取值为'hotkeyChange'。 |
| hotkeyOptions | [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | 是 | 快捷键选项。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<HotkeyOptions> | 是 | 回调函数，返回满足条件的组合按键输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [4200002](../errorcode-inputconsumer.md#4200002-快捷键被系统注册) | The hotkey has been used by the system. |
| [4200003](../errorcode-inputconsumer.md#4200003-快捷键已经被其他应用注册) | The hotkey has been subscribed to by another. |

**示例：**

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
          let leftCtrlKey = 2072;
          let zKey = 2042;
          let hotkeyOptions: inputConsumer.HotkeyOptions = {
            preKeys: [leftCtrlKey],
            finalKey: zKey,
            isRepeat: true
          };
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          };
          try {
            // 订阅热键变更事件
            inputConsumer.on('hotkeyChange', hotkeyOptions, hotkeyCallback);
          } catch (error) {
            console.error(`Failed to Subscribe hot key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## on('keyPressed')

```TypeScript
function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback<KeyEvent>): void
```

订阅按键按下事件。若当前应用窗口为前台焦点窗口，用户按下指定按键，会触发回调。使用callback异步回调。

订阅成功后，该按键事件的系统默认行为将被屏蔽，即不会再触发系统级的响应，如音量调节。要恢复系统响应，请使用[off](arkts-input-inputconsumer-off-f.md#off-3)方法取消订阅。

**起始版本：** 16

<!--Device-inputConsumer-function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback<KeyEvent>): void--><!--Device-inputConsumer-function on(type: 'keyPressed', options: KeyPressedConfig, callback: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyPressed' | 是 | 事件类型，固定取值为'keyPressed'。 |
| options | [KeyPressedConfig](arkts-input-inputconsumer-keypressedconfig-i.md) | 是 | 按键事件消费设置。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<KeyEvent> | 是 | 回调函数，返回按键事件。订阅不同的按键事件需要使用不同的callback，否则订阅不生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { inputConsumer, KeyEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let options: inputConsumer.KeyPressedConfig = {
              key: 16,
              action: 1,
              isRepeat: false,
            }
            // 订阅按键按下事件
            inputConsumer.on('keyPressed', options, (event: KeyEvent) => {
              console.info(`Succeeded in subscribing ${JSON.stringify(event)}.`);
            });
          } catch (error) {
            console.error(`Failed to subscribe , Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

