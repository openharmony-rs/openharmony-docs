# onKeyPressed（系统接口）

## onKeyPressed

```TypeScript
function onKeyPressed(keys: Array<KeyCode>, receiver: Callback<KeyEvent>): void
```

监听指定按键的按下抬起事件，支持监听META\_LEFT键、META\_RIGHT键、电源键、音量键。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onKeyPressed(keys: Array<KeyCode>, receiver: Callback<KeyEvent>): void--><!--Device-inputMonitor-function onKeyPressed(keys: Array<KeyCode>, receiver: Callback<KeyEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;KeyCode&gt; | 是 | 按键码列表，支持如下取值：KEYCODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_META\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEFT、KEYCODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_META\_\_\_ESCAPED\_UNDERSCORE\_\_\_RIGHT、KEYCODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_POWER、KEYCODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_VOLUME\_\_\_ESCAPED\_UNDERSCORE\_\_\_DOWN、KEYCODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_VOLUME\_\_\_ESCAPED\_UNDERSCORE\_\_\_UP。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于接收上报数据的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [4100001](../errorcode-inputmonitor.md#4100001-按键不支持前置监听) | Event listening not supported for the key. |

**示例：**

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor, KeyEvent, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅按键按下事件
            let funCallback = (event: KeyEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            };
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_UP];
            inputMonitor.onKeyPressed(keys, funCallback);
          } catch (error) {
            console.error(`Failed to monitor key pressed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

