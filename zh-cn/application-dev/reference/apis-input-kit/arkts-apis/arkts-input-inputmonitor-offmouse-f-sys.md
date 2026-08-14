# offMouse（系统接口）

## offMouse

```TypeScript
function offMouse(receiver?: Callback<MouseEvent>): void
```

取消监听全局鼠标事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function offMouse(receiver?: Callback<MouseEvent>): void--><!--Device-inputMonitor-function offMouse(receiver?: Callback<MouseEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| receiver | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MouseEvent](arkts-input-multimodalinput-mouseevent-mouseevent-i.md)&gt; | 否 | 需要取消监听的回调函数。若不填，则取消当前应用监听的所有回调函数。 |

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
import { inputMonitor, MouseEvent } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let callback = (mouseEvent: MouseEvent) => {
            console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
          };
          try {
            // 取消监听单个回调函数
            inputMonitor.onMouse(callback);
            inputMonitor.offMouse(callback);
            // 取消监听所有回调函数
            inputMonitor.onMouse((mouseEvent: MouseEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(mouseEvent)}.`);
            });
            inputMonitor.offMouse();
            console.info(`Succeeded in turning off monitor.`);
          } catch (error) {
            console.error(`Failed to monitor the mouse event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

