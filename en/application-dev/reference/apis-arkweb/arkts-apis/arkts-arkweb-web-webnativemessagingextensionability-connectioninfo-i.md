# ConnectionInfo

Represents the information object of the web native messaging connection.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
```

## bundleName

```TypeScript
bundleName: string
```

App package name of the caller, used for identity identification and permission verification. It can be used to determine whether to allow the app to establish a connection or perform message interaction.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## connectionId

```TypeScript
connectionId: number
```

Unique identifier of the connection, used to distinguish and manage different Web native message connections. It can be used to locate a specific connection during logging, status tracking, or resource cleanup.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## extensionOrigin

```TypeScript
extensionOrigin: string
```

Original URL of the caller extension, used for security control and origin identification. It can be used to determine the legitimacy of the extension or implement domain-based access policies.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## fdRead

```TypeScript
fdRead: number
```

Pipe file descriptor used for reading data. Messages can be read from the Web side through this file descriptor.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## fdWrite

```TypeScript
fdWrite: number
```

Pipe file descriptor used for writing data. Messages can be sent to the Web side through this file descriptor.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core
