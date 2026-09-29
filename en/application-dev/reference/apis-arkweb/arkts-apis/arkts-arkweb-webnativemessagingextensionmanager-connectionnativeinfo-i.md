# ConnectionNativeInfo

```TypeScript
interface ConnectionNativeInfo
```

Represents the information about the web native message connection.

**Since:** 21

<!--Device-webNativeMessagingExtensionManager-interface ConnectionNativeInfo--><!--Device-webNativeMessagingExtensionManager-interface ConnectionNativeInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the web native message extension application.

**Type:** string

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionNativeInfo-bundleName: string--><!--Device-ConnectionNativeInfo-bundleName: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## connectionId

```TypeScript
connectionId: number
```

Unique identifier of the Web native message extension connection, returned by connectNative() and used to identify and manage the connection.

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionNativeInfo-connectionId: number--><!--Device-ConnectionNativeInfo-connectionId: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## extensionOrigin

```TypeScript
extensionOrigin: string
```

Source URL of the browser extension.

**Type:** string

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionNativeInfo-extensionOrigin: string--><!--Device-ConnectionNativeInfo-extensionOrigin: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## extensionPid

```TypeScript
extensionPid: number
```

Process ID of the web native message extension.

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

<!--Device-ConnectionNativeInfo-extensionPid: number--><!--Device-ConnectionNativeInfo-extensionPid: number-End-->

**System capability:** SystemCapability.Web.Webview.Core
