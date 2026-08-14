# onTouchscreenSwipe（系统接口）

## onTouchscreenSwipe

```TypeScript
function onTouchscreenSwipe(fingers: int, receiver: Callback<TouchGestureEvent>): void
```

监听触摸屏滑动手势事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onTouchscreenSwipe(fingers: int, receiver: Callback<TouchGestureEvent>): void--><!--Device-inputMonitor-function onTouchscreenSwipe(fingers: int, receiver: Callback<TouchGestureEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fingers | int | 是 | 滑动手势的手指数，取值范围：[3,5]。 |
| receiver | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TouchGestureEvent](arkts-input-multimodalinput-gestureevent-touchgestureevent-i-sys.md)&gt; | 是 | 回调函数，异步上报触摸屏滑动手势事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

## 示例

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor } from '@kit.InputKit';
import { TouchGestureEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅触摸屏滑动事件
            let funCallback = (event: TouchGestureEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(event)}.`);
            };
            let fingers: int = 4;
            inputMonitor.onTouchscreenSwipe(fingers, funCallback);
          } catch (error) {
            console.error(`Failed to monitor touch screen swipe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

