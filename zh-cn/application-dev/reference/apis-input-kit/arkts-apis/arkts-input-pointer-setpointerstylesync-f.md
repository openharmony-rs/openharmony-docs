# setPointerStyleSync

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerStyleSync

```TypeScript
function setPointerStyleSync(windowId: int, pointerStyle: PointerStyle): void
```

设置指定窗口的鼠标样式类型，使用同步方式返回结果。此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅 [setCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)。

**起始版本：** 23

<!--Device-pointer-function setPointerStyleSync(windowId: int, pointerStyle: PointerStyle): void--><!--Device-pointer-function setPointerStyleSync(windowId: int, pointerStyle: PointerStyle): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 是 | 窗口ID。取值范围为大于等于0的整数。<br>窗口ID合法并且对应窗口存在时，可以设置窗口的鼠标光标样式。<br>窗口ID合法但窗口不存在时，也可以设置鼠标光标样式。<br>设置 结果可通过[getPointerStyleSync](arkts-input-pointer-getpointerstylesync-f.md)获取。 |
| pointerStyle | PointerStyle | 是 | 鼠标样式。不能传入DEVELOPER_DEFINED_ICON作为参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. <br> When the windowId value is -1, the system permission is required to set the global style. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 获取应用内最近一个窗口
          window.getLastWindow(this.getUIContext().getHostContext(), (error: BusinessError, win: window.Window) => {
            if (error.code) {
              console.error(`Failed to obtain the top window, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              return;
            }
            let windowId = win.getWindowProperties().id;
            if (windowId < 0) {
              console.info(`Invalid windowId.`);
              return;
            }
            try {
              // 同步设置鼠标指针样式
              pointer.setPointerStyleSync(windowId, pointer.PointerStyle.CROSS);
              console.info(`Succeeded in setting pointer style.`);
            } catch (error) {
              console.error(`Failed to set pointer style, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            }
          });
        })
    }
  }
}
```

ArkTS-Sta示例:

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 此次根据实际获取窗口id
          let windowId: int = 100;
          try {
            // 同步设置鼠标指针样式
            pointer.setPointerStyleSync(windowId, pointer.PointerStyle.CROSS);
            console.info(`Succeeded in setting pointer style.`);
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

