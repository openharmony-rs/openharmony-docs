# onKeyPressed

## onKeyPressed

```TypeScript
function onKeyPressed(options: KeyPressedConfig, callback: Callback<KeyEvent>): void
```

订阅按键按下事件，使用callback异步回调。若当前应用窗口为前台焦点窗口，用户按下指定按键，会触发回调。 订阅成功后，该按键事件的系统默认行为将被屏蔽，即不会再触发系统级的响应，如音量调节。要恢复系统响应，请使用off方法取消订阅。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputConsumer-function onKeyPressed(options: KeyPressedConfig, callback: Callback<KeyEvent>): void--><!--Device-inputConsumer-function onKeyPressed(options: KeyPressedConfig, callback: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Key consumption settings. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | Callback used to return key events. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputConsumer, KeyEvent } from '@kit.InputKit';

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
            inputConsumer.onKeyPressed(options, (event: KeyEvent) => {
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

