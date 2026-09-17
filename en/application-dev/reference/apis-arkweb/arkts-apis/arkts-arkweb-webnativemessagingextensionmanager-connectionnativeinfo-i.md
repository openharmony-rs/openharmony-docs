# ConnectionNativeInfo

Represents the information about the web native message connection.

**Since:** 21

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

**System capability:** SystemCapability.Web.Webview.Core

## connectionId

```TypeScript
connectionId: number
```

Unique identifier of the Web native message extension connection, returned by connectNative() and used to identify and manage the connection.

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## extensionOrigin

```TypeScript
extensionOrigin: string
```

Source URL of the browser extension.

**Type:** string

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## extensionPid

```TypeScript
extensionPid: number
```

Process ID of the web native message extension.

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
