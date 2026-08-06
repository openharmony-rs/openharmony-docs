# offTouchscreenPinch（系统接口）

## offTouchscreenPinch

```TypeScript
function offTouchscreenPinch(fingers: int, receiver?: Callback<TouchGestureEvent>): void
```

取消监听触摸屏捏合手势事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function offTouchscreenPinch(fingers: int, receiver?: Callback<TouchGestureEvent>): void--><!--Device-inputMonitor-function offTouchscreenPinch(fingers: int, receiver?: Callback<TouchGestureEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fingers | int | 是 | 捏合手势的手指数，取值范围：[4,5]。 |
| receiver | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TouchGestureEvent&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types.3.Parameter verification failed. |

**示例：**

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@ohos.multimodalInput.gestureEvent';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let funCallback = (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            };
            let fingers: int = 4;
            inputMonitor.onTouchscreenPinch(fingers, funCallback);
            // 取消监听单个回调函数
            inputMonitor.offTouchscreenPinch(fingers, funCallback);
            inputMonitor.onTouchscreenPinch(fingers, (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            });
            // 取消监听所有回调函数
            inputMonitor.offTouchscreenPinch(fingers);
          } catch (error) {
            console.error(`Failed to cancel monitor touch screen pinch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

