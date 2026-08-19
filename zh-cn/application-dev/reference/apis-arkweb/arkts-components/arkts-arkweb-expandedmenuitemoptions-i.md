# ExpandedMenuItemOptions

自定义菜单扩展项。

**起始版本：** 12

**废弃版本：** 20

**替代接口：** [editMenuOptions](arkts-arkweb-web-attribute.md#editmenuoptions)

<!--Device-unnamed-declare interface ExpandedMenuItemOptions--><!--Device-unnamed-declare interface ExpandedMenuItemOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## action

```TypeScript
action: (selectedText: {plainText: string}) => void
```

回调函数，用于接收用户选择菜单扩展项后的操作。回调参数selectedText包含plainText字段，表示用户选中的文本内容。

**类型：** (selectedText: {plainText: string}) =&gt; void

**起始版本：** 12

**废弃版本：** 20

**替代接口：** EditMenuOptions

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExpandedMenuItemOptions-action: (selectedText: {plainText: string}) => void--><!--Device-ExpandedMenuItemOptions-action: (selectedText: {plainText: string}) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## content

```TypeScript
content: ResourceStr
```

显示内容。

**类型：** ResourceStr

**起始版本：** 12

**废弃版本：** 20

**替代接口：** EditMenuOptions

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExpandedMenuItemOptions-content: ResourceStr--><!--Device-ExpandedMenuItemOptions-content: ResourceStr-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## startIcon

```TypeScript
startIcon?: ResourceStr
```

显示图标。默认值为空，不显示图标。

**类型：** ResourceStr

**起始版本：** 12

**废弃版本：** 20

**替代接口：** EditMenuOptions

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ExpandedMenuItemOptions-startIcon?: ResourceStr--><!--Device-ExpandedMenuItemOptions-startIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.Web.Webview.Core

