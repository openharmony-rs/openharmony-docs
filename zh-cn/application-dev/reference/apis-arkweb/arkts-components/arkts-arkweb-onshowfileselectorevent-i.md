# OnShowFileSelectorEvent

定义文件选择器结果的回调信息，包括结果和参数详情。

**起始版本：** 12

<!--Device-unnamed-declare interface OnShowFileSelectorEvent--><!--Device-unnamed-declare interface OnShowFileSelectorEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## fileSelector

```TypeScript
fileSelector: FileSelectorParam
```

文件选择器的相关信息。

**类型：** [FileSelectorParam](arkts-arkweb-fileselectorparam-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnShowFileSelectorEvent-fileSelector: FileSelectorParam--><!--Device-OnShowFileSelectorEvent-fileSelector: FileSelectorParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: FileSelectorResult
```

用于通知Web组件文件选择的结果。

**类型：** [FileSelectorResult](arkts-arkweb-fileselectorresult-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnShowFileSelectorEvent-result: FileSelectorResult--><!--Device-OnShowFileSelectorEvent-result: FileSelectorResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

