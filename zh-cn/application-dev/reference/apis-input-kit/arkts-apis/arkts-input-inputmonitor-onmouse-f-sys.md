# onMouse（系统接口）

## onMouse

```TypeScript
function onMouse(receiver: Callback<MouseEvent>): void
```

监听全局鼠标事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onMouse(receiver: Callback<MouseEvent>): void--><!--Device-inputMonitor-function onMouse(receiver: Callback<MouseEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| receiver | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MouseEvent](arkts-input-multimodalinput-mouseevent-mouseevent-i.md)&gt; | 是 | 回调函数，异步上报鼠标输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅鼠标事件
            inputMonitor.onMouse((mouseEvent: MouseEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## onMouse

```TypeScript
function onMouse(rect: display.Rect[], receiver: Callback<MouseEvent>): void
```

监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onMouse(rect: display.Rect[], receiver: Callback<MouseEvent>): void--><!--Device-inputMonitor-function onMouse(rect: display.Rect[], receiver: Callback<MouseEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | display.Rect[] | 是 | 可以触发回调任务的矩形区域，可传入1至2个。 |
| receiver | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MouseEvent](arkts-input-multimodalinput-mouseevent-mouseevent-i.md)&gt; | 是 | 回调函数，异步上报鼠标输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |

## 示例

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';
import { inputMonitor } from '@kit.InputKit';
import { MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let rect: Array<display.Rect> = [{ left: 100, top: 100, width: 100, height: 100 },
            { left: 600, top: 100, width: 100, height: 100
          }];
          let callback = (mouseEvent : MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
          }

          try {
            // 订阅鼠标事件
            inputMonitor.onMouse(rect, callback);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

