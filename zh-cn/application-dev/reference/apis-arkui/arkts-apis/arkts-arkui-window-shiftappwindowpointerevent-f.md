# shiftAppWindowPointerEvent

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
import { floatView } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';
```

## shiftAppWindowPointerEvent

```TypeScript
function shiftAppWindowPointerEvent(sourceWindowId: int, targetWindowId: int): Promise<void>
```

主窗口和子窗口可正常调用，用于将鼠标输入事件从源窗口转移到目标窗口。使用Promise异步回调。 源窗口仅在[onTouch](../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#ontouch)事件（事件类型必须为 TouchType.Down）的回调方法中调用此接口才会有鼠标输入事件转移效果，成功调用此接口后，系统会向源窗口补发鼠标按键抬起（TouchType.Up）事件，并且向目标窗口补发鼠标按键按下（TouchType.Down）事件。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-window-function shiftAppWindowPointerEvent(sourceWindowId: int, targetWindowId: int): Promise<void>--><!--Device-window-function shiftAppWindowPointerEvent(sourceWindowId: int, targetWindowId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceWindowId | int | 是 | 源窗口id。推荐使用 [getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties)方法获取窗口id属性。 |
| targetWindowId | int | 是 | 目标窗口id。推荐使用 [getWindowProperties()](arkts-arkui-window-window-i.md#getwindowproperties)方法获取窗口id属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Failed to convert parameter to sourceWindowId; 3. Failed to convert parameter to targetWindowId; 4. Invalid sourceWindowId or targetWindowId. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: 1. SourceWindow cannot find: not created or not belong to current process; 2. TargetWindow cannot find: not created or not belong to current process; 3. Internal task error. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: 1. Invalid window type. Only main windows and subwindows are supported; 2. The two windows are not from the same process. |

**示例**

ArkTS-Dyn示例：

```TypeScript
// ets/pages/Index.ets
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Blank('160')
          .color(Color.Blue)
          .onTouch((event: TouchEvent) => {
            if (event.type === TouchType.Down) {
              try {
                let sourceWindowId = 1;
                let targetWindowId = 2;
                let promise = window.shiftAppWindowPointerEvent(sourceWindowId, targetWindowId);
                promise.then(() => {
                  console.info('Succeeded in shifting app window pointer event');
                }).catch((err: BusinessError) => {
                  console.error(`Failed to shift app window pointer event. Cause code: ${err.code}, message: ${err.message}`);
                });
              } catch (exception) {
                console.error(`Failed to shift app pointer event. Cause code: ${exception.code}, message: ${exception.message}`);
              }
            }
          })
      }.width('100%')
    }.height('100%').width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
// ets/pages/Index.ets
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Blank('160')
          .color(Color.Blue)
          .onTouch((event: TouchEvent) => {
            if (event.type === TouchType.Down) {
              try {
                let sourceWindowId = 1;
                let targetWindowId = 2;
                let promise = window.shiftAppWindowPointerEvent(sourceWindowId, targetWindowId);
                promise.then(() => {
                  console.info('Succeeded in shifting app window pointer event');
                }).catch((err) => {
                  console.error(`Failed to shift app window pointer event. Cause code: ${err.code}, message: ${err.message}`);
                });
              } catch (exception) {
                let err = exception as BusinessError;
                console.error(`Failed to shift app pointer event. Cause code: ${err.code}, message: ${err.message}`);
              }
            }
          })
      }.width('100%')
    }.height('100%').width('100%')
  }
}
```

