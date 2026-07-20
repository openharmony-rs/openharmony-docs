# injectTouchEvent（系统接口）

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

<a id="injecttouchevent"></a>
## injectTouchEvent

```TypeScript
function injectTouchEvent(touchEvent: TouchEventData): void
```

触屏输入事件注入。

**起始版本：** 11

**需要权限：** 
- API版本12+：ohos.permission.INJECT_INPUT_EVENT

<!--Device-inputEventClient-function injectTouchEvent(touchEvent: TouchEventData): void--><!--Device-inputEventClient-function injectTouchEvent(touchEvent: TouchEventData): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| touchEvent | [TouchEventData](arkts-input-inputeventclient-toucheventdata-i-sys.md) | 是 | 触屏注入描述信息。此参数中[Action](arkts-input-multimodalinput-touchevent-action-e.md)属性不支持设置为CANCEL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputEventClient } from '@kit.InputKit';
import { Touch, TouchEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let touchEvent: Touch = {
              id: 1,
              pressedTime: 1,
              screenX: 0,
              screenY: 0,
              windowX: 0,
              windowY: 0,
              pressure: 0,
              width: 0,
              height: 0,
              tiltX: 0,
              tiltY: 0,
              toolX: 0,
              toolY: 0,
              toolWidth: 0,
              toolHeight: 0,
              rawX: 0,
              rawY: 0,
              toolType: 0,
            };

            let touchEventUpData: TouchEvent = {
              action: 3,
              sourceType: 0,
              touch: touchEvent,
              touches: [],
              id: 0,
              deviceId: 0,
              actionTime: 0,
              screenId: 0,
              windowId: 0
            };
            ;
            let touchEventUp: inputEventClient.TouchEventData = {
              touchEvent: touchEventUpData
            };
            // 注入触摸事件
            inputEventClient.injectTouchEvent(touchEventUp);

            let touchEventDownData: TouchEvent = {
              action: 1,
              sourceType: 0,
              touch: touchEvent,
              touches: [],
              id: 0,
              deviceId: 0,
              actionTime: 0,
              screenId: 0,
              windowId: 0
            };
            ;
            let touchEventDown: inputEventClient.TouchEventData = {
              touchEvent: touchEventDownData
            }
            // 注入触摸事件
            inputEventClient.injectTouchEvent(touchEventDown);
          } catch (error) {
            console.error(`Failed to inject touchEvent, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

