# findWindow

## findWindow

```TypeScript
function findWindow(name: string): Window
```

查找指定名称对应的窗口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-window-function findWindow(name: string): Window--><!--Device-window-function findWindow(name: string): Window-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 窗口名称。查找子窗口或系统窗口时使用[Configuration](arkts-arkui-window-configuration-i.md#Configuration)中的窗口名称；查找主窗口时使用 [getWindowName](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getWindowName)获取当前实例的窗口名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Window](arkts-arkui-window-window-i.md) | 当前查找的窗口对象。如果查找指定名称对应的窗口不存在，会抛出1300002错误码 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause: 1. The window is not created or destroyed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
let windowClass: window.Window | undefined = undefined;
try {
  windowClass = window.findWindow('test');
} catch (exception) {
  console.error(`Failed to find the Window. Cause code: ${exception.code}, message: ${exception.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
let windowClass: window.Window | undefined = undefined;
try {
  windowClass = window.findWindow('test');
} catch (err: Error) {
  console.error(`Failed to find the Window. Cause code: ${err.code}, message: ${err.message}`);
}
```

