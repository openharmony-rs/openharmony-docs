# FileSelectorResult

FileSelectorResult是ArkWeb组件中用于通知Web组件文件选择结果的类，支持应用层自定义文件选择行为、统一文件选择结果回传机制，适用于应用需要接管文件选择流程的场景，例如拉起系统文件选择器、图库选择器或相机选择器 后，将选中的文件结果返回给Web页面。当Web组件中的HTML页面通过`&lt;input type="file"&gt;`等方式发起文件选择请求时，应用可通过FileSelectorResult将用户选择的文件列表回传给Web组件，完成文件选择 流程。该类主要在`onShowFileSelector`事件回调中使用，使应用能够灵活控制文件选择交互，提升用户体验的一致性。示例代码参考 [onShowFileSelector](arkts-arkweb-web-attribute.md#onshowfileselector)。

**起始版本：** 9

<!--Device-unnamed-declare class FileSelectorResult--><!--Device-unnamed-declare class FileSelectorResult-End-->

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

FileSelectorResult的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorResult-constructor()--><!--Device-FileSelectorResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleFileList

```TypeScript
handleFileList(fileList: Array<string>): void
```

通过传入的文件列表（fileList）通知Web组件用户选择的文件，完成文件选择流程。Web组件可以使用传入的文件列表进行后续处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorResult-handleFileList(fileList: Array<string>): void--><!--Device-FileSelectorResult-handleFileList(fileList: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileList | Array&lt;string&gt; | 是 | 文件URI字符串数组，用于向Web组件传递用户选择的文件路径。 |

