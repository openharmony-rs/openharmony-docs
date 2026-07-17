# PiPController

画中画控制器实例。用于启动、停止画中画以及更新回调注册等。

下列API示例中都需先使用[PiPWindow.create()](arkts-arkui-pipwindow-create-f.md#create-1)方法获取到PiPController实例，再通过此实例调用对应方法。

**起始版本：** 11

<!--Device-PiPWindow-interface PiPController--><!--Device-PiPWindow-interface PiPController-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## isPiPSupported

```TypeScript
isPiPSupported(): boolean
```

Returns a Boolean value that indicates whether picture-in-picture is supported

**起始版本：** 18

<!--Device-PiPController-isPiPSupported(): boolean--><!--Device-PiPController-isPiPSupported(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - True if picture-in-picture is supported, otherwise false |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [1300014](../errorcode-window.md#1300014-画中画内部错误) | PiP internal error. |

