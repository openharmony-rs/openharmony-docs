# off

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## off('hotkeyChange')

```TypeScript
function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback<HotkeyOptions>): void
```

取消订阅应用快捷键。使用callback异步回调。

**起始版本：** 14

<!--Device-inputConsumer-function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback<HotkeyOptions>): void--><!--Device-inputConsumer-function off(type: 'hotkeyChange', hotkeyOptions: HotkeyOptions, callback?: Callback<HotkeyOptions>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotkeyChange' | 是 | 事件类型，固定取值为'hotkeyChange'。 |
| hotkeyOptions | [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | 是 | 快捷键选项。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<HotkeyOptions> | 否 | 需要取消订阅的回调函数。若缺省，则取消当前应用快捷键选项已订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

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
          // 取消订阅单个应用快捷键回调函数
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          };
          let hotkeyOption: inputConsumer.HotkeyOptions = { preKeys: [leftCtrlKey], finalKey: zKey, isRepeat: true };
          try {
            // 订阅热键变更事件
            inputConsumer.on('hotkeyChange', hotkeyOption, hotkeyCallback);
            // 取消订阅热键变更事件
            inputConsumer.off('hotkeyChange', hotkeyOption, hotkeyCallback);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

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
          // 取消订阅所有应用快捷键回调函数
          let hotkeyCallback = (hotkeyOptions: inputConsumer.HotkeyOptions) => {
            console.info(`Succeeded in consuming hotkey, hotkeyOptions: ${JSON.stringify(hotkeyOptions)}.`);
          };
          let hotkeyOption: inputConsumer.HotkeyOptions = { preKeys: [leftCtrlKey], finalKey: zKey, isRepeat: true };
          try {
            // 订阅热键变更事件
            inputConsumer.on('hotkeyChange', hotkeyOption, hotkeyCallback);
            // 取消订阅热键变更事件
            inputConsumer.off('hotkeyChange', hotkeyOption);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## off('keyPressed')

```TypeScript
function off(type: 'keyPressed', callback?: Callback<KeyEvent>): void
```

取消对'keyPressed'事件的订阅，使用callback异步回调。调用该方法后，被屏蔽的系统按键默认行为将恢复，即系统对音量调节等默认响应将恢复。

**起始版本：** 16

<!--Device-inputConsumer-function off(type: 'keyPressed', callback?: Callback<KeyEvent>): void--><!--Device-inputConsumer-function off(type: 'keyPressed', callback?: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyPressed' | 是 | 事件类型，固定取值为'keyPressed'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<KeyEvent> | 否 | 需要取消订阅的回调函数。若缺省，则取消当前已订阅的所有回调函数。 |

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
            // 取消指定回调函数
            let options: inputConsumer.KeyPressedConfig = {
              key: 16,
              action: 1,
              isRepeat: false,
            }
            let callback = (event: KeyEvent) => {
              console.info(`Succeeded in unsubscribing ${JSON.stringify(event)}.`);
            };
            // 订阅按键按下事件
            inputConsumer.on('keyPressed', options, callback);
            // 取消订阅按键按下事件
            inputConsumer.off('keyPressed', callback);
            // 取消当前已订阅的所有回调函数
            inputConsumer.off('keyPressed');
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

