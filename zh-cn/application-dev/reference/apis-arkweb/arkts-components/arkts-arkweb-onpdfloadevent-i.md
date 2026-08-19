# OnPdfLoadEvent

定义PDF加载成功或失败时触发的函数。

**起始版本：** 20

<!--Device-unnamed-declare interface OnPdfLoadEvent--><!--Device-unnamed-declare interface OnPdfLoadEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## result

```TypeScript
result: PdfLoadResult
```

PDF页面加载结果。

**类型：** [PdfLoadResult](arkts-arkweb-pdfloadresult-e.md)

**起始版本：** 20

<!--Device-OnPdfLoadEvent-result: PdfLoadResult--><!--Device-OnPdfLoadEvent-result: PdfLoadResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

页面的URL地址。

**类型：** string

**起始版本：** 20

<!--Device-OnPdfLoadEvent-url: string--><!--Device-OnPdfLoadEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

