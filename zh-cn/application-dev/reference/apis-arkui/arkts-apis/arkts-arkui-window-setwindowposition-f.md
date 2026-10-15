# setWindowPosition

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## setWindowPosition

```TypeScript
function setWindowPosition(list: Array<WindowPositionParams>): Promise<void>
```

调整当前应用进程中一个或多个主窗口的z序。使用Promise异步回调。

支持的调整方式如下：  
- 将一个主窗口置于另一个主窗口下方。  
- 将一个主窗口置于所有应用窗口的底部。  
- 将一个主窗口置于所有应用窗口的顶部。  
- 将一个主窗口切换为全局置顶状态或取消全局置顶状态。

设置全局置顶状态需要ohos.permission.WINDOW_TOPMOST权限。

不支持调整位于[虚拟屏](../../../displaymanager/display-terminology.md#虚拟屏)上的主窗口的z序。若待调整的窗口或insertAfter指定的目标主窗口位于虚拟屏上，将抛出1300008错误码。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.WINDOW_TOPMOST

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-window-function setWindowPosition(list: Array<WindowPositionParams>): Promise<void>--><!--Device-window-function setWindowPosition(list: Array<WindowPositionParams>): Promise<void>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| list | Array&lt;[WindowPositionParams](arkts-arkui-window-windowpositionparams-i.md)&gt; | 是 | 待调整的窗口位置选项列表。该列表不能为空，且最大个数不能超过50个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:         1. The window to be adjusted cannot be found: not created, has been destroyed or not belong to current process;         2. The target main window specified by insertAfter cannot be found: not created or has been destroyed. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300004](../errorcode-window.md#1300004-无权限操作) | Unauthorized operation. Possible cause: Invalid window type. Only main windows are supported. |
| [1300008](../errorcode-window.md#1300008-显示设备异常) | The display device is abnormal. Possible cause: The window to be adjusted or the target main window specified by insertAfter is on a virtual screen. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error. Possible cause: The windowPositions list exceeds the maximum size of 50. |
