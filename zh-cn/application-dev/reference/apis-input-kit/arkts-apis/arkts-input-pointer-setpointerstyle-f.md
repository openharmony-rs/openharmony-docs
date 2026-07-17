# setPointerStyle

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerStyle

```TypeScript
function setPointerStyle(windowId: number, pointerStyle: PointerStyle, callback: AsyncCallback<void>): void
```

设置指定窗口的鼠标样式类型，此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅[setCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)，使用callback异步回调。

**起始版本：** 9

<!--Device-pointer-function setPointerStyle(windowId: int, pointerStyle: PointerStyle, callback: AsyncCallback<void>): void--><!--Device-pointer-function setPointerStyle(windowId: int, pointerStyle: PointerStyle, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 窗口ID。取值范围为大于等于0的整数。<br>窗口ID合法并且对应窗口存在时，可以设置窗口的鼠标光标样式。<br>窗口ID合法但窗口不存在时，也可以设置鼠标光标样式。<br>设置结果可通过[getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getpointerstyle-1)获取。 |
| pointerStyle | [PointerStyle](../../apis-arkui/arkts-apis/arkts-arkui-pointerstyle-t.md) | 是 | 鼠标样式。 不能传入DEVELOPER_DEFINED_ICON作为参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置鼠标样式类型成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br> When the windowId value is -1, the system permission is required to set the global style.**ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

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
              // 设置鼠标指针样式
              pointer.setPointerStyle(windowId, pointer.PointerStyle.CROSS, error => {
                console.info(`Succeeded in setting pointer style.`);
              });
            } catch (error) {
              console.error(`Failed to set pointer style, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            }
          });
        })
    }
  }
}

```


## setPointerStyle

```TypeScript
function setPointerStyle(windowId: number, pointerStyle: PointerStyle): Promise<void>
```

设置指定窗口的鼠标样式类型，此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅[setCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)，使用Promise异步回调。

**起始版本：** 9

<!--Device-pointer-function setPointerStyle(windowId: int, pointerStyle: PointerStyle): Promise<void>--><!--Device-pointer-function setPointerStyle(windowId: int, pointerStyle: PointerStyle): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 窗口ID。取值范围为大于等于0的整数。<br>窗口ID合法并且对应窗口存在时，可以设置窗口的鼠标光标样式。<br>窗口ID合法但窗口不存在时，也可以设置鼠标光标样式。<br>设置结果可通过[getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getpointerstyle-2)获取。 |
| pointerStyle | [PointerStyle](../../apis-arkui/arkts-apis/arkts-arkui-pointerstyle-t.md) | 是 | 鼠标样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br> When the windowId value is -1, the system permission is required to set the global style.**ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

**示例：**

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
              // 设置鼠标指针样式
              pointer.setPointerStyle(windowId, pointer.PointerStyle.CROSS).then(() => {
                console.info(`Succeeded in setting pointer style.`);
              }).catch((error: BusinessError) => {
                console.error(`Failed to set pointer style, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              });
            } catch (error) {
              console.error(`Failed to set pointer style, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            }
          });
        })
    }
  }
}

```

