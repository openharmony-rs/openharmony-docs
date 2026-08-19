# DataResubmissionHandler

DataResubmissionHandler是Web组件中处理网页表单数据重新提交的处理类。当网页需要重新提交之前已发送的表单数据时，Web组件会通过`onDataResubmitted`事件回调提供 DataResubmissionHandler实例给应用，允许应用决定是否重新提交表单数据或取消导航。

**起始版本：** 9

<!--Device-unnamed-declare class DataResubmissionHandler--><!--Device-unnamed-declare class DataResubmissionHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## cancel

```TypeScript
cancel(): void
```

取消重新发送表单数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataResubmissionHandler-cancel(): void--><!--Device-DataResubmissionHandler-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

DataResubmissionHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataResubmissionHandler-constructor()--><!--Device-DataResubmissionHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resend

```TypeScript
resend(): void
```

重新发送表单数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataResubmissionHandler-resend(): void--><!--Device-DataResubmissionHandler-resend(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

