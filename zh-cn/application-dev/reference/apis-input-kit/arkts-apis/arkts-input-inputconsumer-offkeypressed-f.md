# offKeyPressed

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## offKeyPressed

```TypeScript
function offKeyPressed(callback?: Callback<KeyEvent>): void
```

取消对'keyPressed'事件的订阅，使用callback异步回调。调用该方法后，被屏蔽的系统按键默认行为将恢复，即系统对音量调节等默认响应将恢复。

**起始版本：** 23

<!--Device-inputConsumer-function offKeyPressed(callback?: Callback<KeyEvent>): void--><!--Device-inputConsumer-function offKeyPressed(callback?: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[KeyEvent](arkts-input-multimodalinput-keyevent-keyevent-i.md)&gt; | 否 | 需要取消订阅的回调函数。若缺省，则取消当前已订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

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
            let callback = (event: KeyEvent) => {
              console.info(`Subscribe success ${JSON.stringify(event)}`);
            };
            inputConsumer.onKeyPressed(options, callback);
            // 取消指定回调函数
            inputConsumer.offKeyPressed(callback);
            // 取消当前已订阅的所有回调函数
            inputConsumer.offKeyPressed();
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

