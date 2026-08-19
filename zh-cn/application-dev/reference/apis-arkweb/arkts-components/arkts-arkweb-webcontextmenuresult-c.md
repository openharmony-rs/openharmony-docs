# WebContextMenuResult

WebContextMenuResult是ArkWeb组件中用于处理上下文菜单（长按页面元素或鼠标右键弹出菜单）事件的类。它为开发者提供了一系列菜单操作的执行能力，包括文本编辑操作（复制、粘贴、剪切、全选、撤销、重做、粘贴并匹配样式） 、图片操作（复制图片、保存图片）、菜单控制（关闭菜单）以及密码自动填充功能。 开发者通常在需要自定义Web组件上下文菜单行为时使用WebContextMenuResult。通过`onContextMenuShow`事件回调获取WebContextMenuResult实例，结合 WebContextMenuParam提供的菜单上下文信息，判断用户操作场景并调用相应的响应方法，从而实现自定义菜单交互逻辑。若开发者不执行任何菜单响应操作，则必须调用`closeContextMenu`方法关闭菜单。 示例代码参考[onContextMenuShow&lt;sup&gt;9+&lt;/sup&gt;](arkts-arkweb-web-attribute.md#oncontextmenushow)。

**起始版本：** 9

<!--Device-unnamed-declare class WebContextMenuResult--><!--Device-unnamed-declare class WebContextMenuResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## closeContextMenu

```TypeScript
closeContextMenu(): void
```

不执行WebContextMenuResult其他接口操作时，需要调用此接口关闭菜单。 > **说明：** > > 调用说明： > > - 调用WebContextMenuResult的其他方法（如copy、paste、cut等）完成操作后，应调用此方法关闭菜单。 > > - 如果不再需要执行其他菜单操作，也应及时调用此方法关闭菜单。 > > - 未调用此方法可能导致菜单资源未正确释放。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-closeContextMenu(): void--><!--Device-WebContextMenuResult-closeContextMenu(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebContextMenuResult的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-constructor()--><!--Device-WebContextMenuResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## copy

```TypeScript
copy(): void
```

执行复制文本操作。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-copy(): void--><!--Device-WebContextMenuResult-copy(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## copyImage

```TypeScript
copyImage(): void
```

当WebContextMenuParam包含图片内容时，用于复制该图片到剪贴板，从API version 24开始支持对canvas图片进行复制。若需保存图片到本地文件，应使用saveImage()方法。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-copyImage(): void--><!--Device-WebContextMenuResult-copyImage(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## cut

```TypeScript
cut(): void
```

执行剪切操作。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-cut(): void--><!--Device-WebContextMenuResult-cut(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## paste

```TypeScript
paste(): void
```

执行粘贴操作，保留原始格式。若需粘贴纯文本并匹配目标格式，应使用pasteAndMatchStyle()方法。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。 > > 需要配置权限： > [ohos.permission.READ_PASTEBOARD](../../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-paste(): void--><!--Device-WebContextMenuResult-paste(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pasteAndMatchStyle

```TypeScript
pasteAndMatchStyle(): void
```

执行与此上下文菜单相关的粘贴操作，粘贴的内容会匹配目标格式，以纯文本形式呈现。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。 > > 需要配置权限： > [ohos.permission.READ_PASTEBOARD](../../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)。

**起始版本：** 20

<!--Device-WebContextMenuResult-pasteAndMatchStyle(): void--><!--Device-WebContextMenuResult-pasteAndMatchStyle(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## redo

```TypeScript
redo(): void
```

执行重做操作，重新执行被撤销的操作。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 20

<!--Device-WebContextMenuResult-redo(): void--><!--Device-WebContextMenuResult-redo(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## requestPasswordAutoFill

```TypeScript
requestPasswordAutoFill(): void
```

请求密码保险箱中的用户名或密码数据自动填充到当前获得焦点的输入框中。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 23

<!--Device-WebContextMenuResult-requestPasswordAutoFill(): void--><!--Device-WebContextMenuResult-requestPasswordAutoFill(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## saveImage

```TypeScript
saveImage(): void
```

保存上下文菜单相关的图片，调用后将触发下载流程。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebContextMenuResult-saveImage(): void--><!--Device-WebContextMenuResult-saveImage(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## selectAll

```TypeScript
selectAll(): void
```

执行全选操作。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-selectAll(): void--><!--Device-WebContextMenuResult-selectAll(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## undo

```TypeScript
undo(): void
```

执行撤销操作，撤销上一次的编辑操作。 > **说明：** > > 完成操作后，应调用[closeContextMenu](#closecontextmenu)关闭菜单，未调用可能导致菜单资源未正确释放。

**起始版本：** 20

<!--Device-WebContextMenuResult-undo(): void--><!--Device-WebContextMenuResult-undo(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

