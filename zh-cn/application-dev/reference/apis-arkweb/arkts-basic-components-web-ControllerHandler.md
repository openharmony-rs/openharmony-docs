# Class (ControllerHandler)

设置用户新建Web组件的WebviewController对象。示例代码参考[onWindowNew事件](./arkts-basic-components-web-events.md#onwindownew9)。

> **说明：**
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

**系统能力：** SystemCapability.Web.Webview.Core

## constructor<sup>9+</sup>

constructor()

ControllerHandler的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

## setWebController<sup>9+</sup>

setWebController(controller: WebviewController): void

设置WebviewController对象，如果不需要打开新窗口请设置为null。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名        | 类型                                     | 必填 | 说明                                     |
| ---------- | ---------------------------------------- | ---- | ---------------------------------------- |
| controller | [WebviewController](./arkts-apis-webview-WebviewController.md) | 是  | 新建Web组件的WebviewController对象，如果不需要打开新窗口请设置为null。 |