# ControllerHandler

ControllerHandler是ArkWeb提供的处理新建Web组件控制器分配的帮助类。当Web页面通过`window.open`等方式请求创建新窗口，且Web组件已开启 [multiWindowAccess](arkts-arkweb-web-attribute.md#multiwindowaccess)能力时，系统通过[onWindowNew](arkts-arkweb-web-attribute.md#onwindownew)事件将 ControllerHandler对象提供给应用。开发者需调用其[setWebController](#setwebcontroller)方法为新窗口设置有效的 [WebviewController](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md)对象，将新窗口与页面中实际创建的Web组件关联；Web内核在等待 setWebController调用期间会阻塞渲染进程，若应用决定不创建新窗口，必须调用`setWebController(null)`通知Web内核，否则渲染进程会持续阻塞。典型使用场景是在自定义弹窗、新页面或分屏中打开Web新窗 口，并需要应用侧显式管理新窗口的URL展示与安全隔离。

**起始版本：** 9

<!--Device-unnamed-declare class ControllerHandler--><!--Device-unnamed-declare class ControllerHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

ControllerHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ControllerHandler-constructor()--><!--Device-ControllerHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## setWebController

```TypeScript
setWebController(controller: WebviewController): void
```

设置新创建Web组件的WebviewController对象；若应用决定不创建新窗口，必须设置为null通知Web内核，否则会造成渲染进程阻塞。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ControllerHandler-setWebController(controller: WebviewController): void--><!--Device-ControllerHandler-setWebController(controller: WebviewController): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [WebviewController](arkts-arkweb-webviewcontroller-t.md) | 是 | 新建Web组件的WebviewController对象，如果不需要打开新窗口请设置为null。 |

