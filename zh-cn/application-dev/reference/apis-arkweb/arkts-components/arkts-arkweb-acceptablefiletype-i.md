# AcceptableFileType

提供文件选择器推荐的文件类型信息，包括MIME类型和类型数组。

**起始版本：** 23

<!--Device-unnamed-declare interface AcceptableFileType--><!--Device-unnamed-declare interface AcceptableFileType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## acceptableType

```TypeScript
acceptableType: Array<string>
```

文件类型数组，包含若干可供选择的文件类型。

**类型：** Array&lt;string&gt;

**起始版本：** 23

<!--Device-AcceptableFileType-acceptableType: Array<string>--><!--Device-AcceptableFileType-acceptableType: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mimeType

```TypeScript
mimeType: string
```

文件MIME类型。

**类型：** string

**起始版本：** 23

<!--Device-AcceptableFileType-mimeType: string--><!--Device-AcceptableFileType-mimeType: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

