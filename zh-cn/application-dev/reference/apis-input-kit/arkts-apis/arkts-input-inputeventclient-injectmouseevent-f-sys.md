# injectMouseEvent（系统接口）

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## injectMouseEvent

```TypeScript
function injectMouseEvent(mouseEvent: MouseEventData): void
```

鼠标/触控板事件注入。

**起始版本：** 11

**需要权限：** 
- API版本12+：ohos.permission.INJECT_INPUT_EVENT

<!--Device-inputEventClient-function injectMouseEvent(mouseEvent: MouseEventData): void--><!--Device-inputEventClient-function injectMouseEvent(mouseEvent: MouseEventData): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mouseEvent | [MouseEventData](arkts-input-inputeventclient-mouseeventdata-i-sys.md) | 是 | 鼠标/触控板事件注入描述信息。此参数中[Action](arkts-input-multimodalinput-mouseevent-action-e.md)属性不支持设置为CANCEL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputEventClient } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let mouseButtonUpData: MouseEvent = {
              id: 0,
              deviceId: 1,
              actionTime: 2,
              screenId: 1,
              windowId: 0,
              action: 3,
              screenX: 100,
              screenY: 200,
              windowX: 100,
              windowY: 200,
              rawDeltaX: 200,
              rawDeltaY: 200,
              button: 2,
              pressedButtons: [2],
              axes: [],
              pressedKeys: [0],
              ctrlKey: false,
              altKey: false,
              shiftKey: false,
              logoKey: false,
              fnKey: false,
              capsLock: false,
              numLock: false,
              scrollLock: false,
              toolType: 1,
            };
            let mouseButtonUp: inputEventClient.MouseEventData = {
              mouseEvent: mouseButtonUpData
            };
            // 注入鼠标事件
            inputEventClient.injectMouseEvent(mouseButtonUp);

            let mouseButtonDownData: MouseEvent = {
              id: 0,
              deviceId: 1,
              actionTime: 2,
              screenId: 1,
              windowId: 0,
              action: 2,
              screenX: 100,
              screenY: 200,
              windowX: 100,
              windowY: 200,
              rawDeltaX: 200,
              rawDeltaY: 200,
              button: 2,
              pressedButtons: [2],
              axes: [],
              pressedKeys: [0],
              ctrlKey: false,
              altKey: false,
              shiftKey: false,
              logoKey: false,
              fnKey: false,
              capsLock: false,
              numLock: false,
              scrollLock: false,
              toolType: 1,
            };
            let mouseButtonDown: inputEventClient.MouseEventData = {
              mouseEvent: mouseButtonDownData
            };
            // 注入鼠标事件
            inputEventClient.injectMouseEvent(mouseButtonDown);
          } catch (error) {
            console.error(`Failed to inject MouseEvent, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

