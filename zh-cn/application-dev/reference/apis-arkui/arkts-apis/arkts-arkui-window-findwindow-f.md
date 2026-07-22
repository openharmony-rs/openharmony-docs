# findWindow

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## findWindow

```TypeScript
function findWindow(name: string): Window
```

查找指定名称对应的窗口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-window-function findWindow(name: string): Window--><!--Device-window-function findWindow(name: string): Window-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 窗口名称。查找子窗口或系统窗口时使用[Configuration](arkts-arkui-window-configuration-i.md)中的窗口名称；查找主窗口时使用[getWindowName](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getwindowname12)获取当前实例的窗口名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Window](arkts-arkui-window-window-i.md) | 当前查找的窗口对象。如果查找指定名称对应的窗口不存在，会抛出1300002错误码 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: The window is not created or destroyed. |

**示例：**

```TypeScript
let windowClass: window.Window | undefined = undefined;
try {
  windowClass = window.findWindow('test');
} catch (exception) {
  console.error(`Failed to find the Window. Cause code: ${exception.code}, message: ${exception.message}`);
}

```

