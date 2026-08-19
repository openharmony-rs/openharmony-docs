# NativeEmbedParamItem

提供同层渲染object标签内嵌param元素的详细信息，包括状态和参数。适用于需要监控param元素变化的场景，提升同层元素管理的灵活性和准确性。

**起始版本：** 21

<!--Device-unnamed-declare interface NativeEmbedParamItem--><!--Device-unnamed-declare interface NativeEmbedParamItem-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## id

```TypeScript
id: string
```

param元素的id信息。

**类型：** string

**起始版本：** 21

<!--Device-NativeEmbedParamItem-id: string--><!--Device-NativeEmbedParamItem-id: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## name

```TypeScript
name?: string
```

param元素的参数名称。

**类型：** string

**起始版本：** 21

<!--Device-NativeEmbedParamItem-name?: string--><!--Device-NativeEmbedParamItem-name?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## status

```TypeScript
status: NativeEmbedParamStatus
```

param元素的状态变化类型。

**类型：** [NativeEmbedParamStatus](arkts-arkweb-nativeembedparamstatus-e.md)

**起始版本：** 21

<!--Device-NativeEmbedParamItem-status: NativeEmbedParamStatus--><!--Device-NativeEmbedParamItem-status: NativeEmbedParamStatus-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## value

```TypeScript
value?: string
```

param元素的参数值。

**类型：** string

**起始版本：** 21

<!--Device-NativeEmbedParamItem-value?: string--><!--Device-NativeEmbedParamItem-value?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

