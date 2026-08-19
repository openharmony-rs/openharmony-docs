# NativeEmbedParamDataInfo

提供同层渲染object标签内嵌param元素变化时同层标签的详细信息，包括标签ID和参数项。适用于需要监控param元素变化的场景，提升同层元素管理的灵活性和准确性。

**起始版本：** 21

<!--Device-unnamed-declare interface NativeEmbedParamDataInfo--><!--Device-unnamed-declare interface NativeEmbedParamDataInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## embedId

```TypeScript
embedId: string
```

同层标签的唯一id。

**类型：** string

**起始版本：** 21

<!--Device-NativeEmbedParamDataInfo-embedId: string--><!--Device-NativeEmbedParamDataInfo-embedId: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## objectAttributeId

```TypeScript
objectAttributeId?: string
```

同层标签的id信息。

**类型：** string

**起始版本：** 21

<!--Device-NativeEmbedParamDataInfo-objectAttributeId?: string--><!--Device-NativeEmbedParamDataInfo-objectAttributeId?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## paramItems

```TypeScript
paramItems?: Array<NativeEmbedParamItem>
```

发生变化的param元素的详细信息，包括每一个param元素的状态变化类型、id、参数名称和参数值。

**类型：** Array&lt;[NativeEmbedParamItem](arkts-arkweb-nativeembedparamitem-i.md)&gt;

**起始版本：** 21

<!--Device-NativeEmbedParamDataInfo-paramItems?: Array<NativeEmbedParamItem>--><!--Device-NativeEmbedParamDataInfo-paramItems?: Array<NativeEmbedParamItem>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

