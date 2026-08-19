# onRotate（系统接口）

## 导入模块

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## onRotate

```TypeScript
function onRotate(fingers: int, receiver: Callback<Rotate>): void
```

监听全局触控板的旋转事件。

**起始版本：** 23

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onRotate(fingers: int, receiver: Callback<Rotate>): void--><!--Device-inputMonitor-function onRotate(fingers: int, receiver: Callback<Rotate>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fingers | int | 是 | 旋转的手指数，目前支持监听手指数是2。 |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[Rotate](arkts-input-multimodalinput-gestureevent-rotate-i.md)&gt; | 是 | 回调函数，返回旋转输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |

**示例**

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor } from '@kit.InputKit';
import { Rotate } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 旋转手势监听手指数2
            inputMonitor.onRotate(2, (rotateEvent: Rotate) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(rotateEvent)}.`);
              return false;
            });
          } catch (error) {
            console.error(`Failed to monitor rotate event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

