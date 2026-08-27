# BlurOnKeyboardHideMode

设置手动收起软键盘时Web元素是否失焦。

**起始版本：** 14

**系统能力：** SystemCapability.Web.Webview.Core

## SILENT

```TypeScript
SILENT = 0
```

软键盘收起时Web组件失焦功能关闭，当用户手动收起软键盘时焦点仍在文本框。适用于需要保持输入焦点的场景。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## BLUR

```TypeScript
BLUR = 1
```

软键盘收起时Web组件失焦功能开启，当用户手动收起软键盘时，焦点会从文本框转移到Web的body上，文本框失焦。适用于需要标准输入框行为的场景。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
