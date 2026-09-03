# @ohos.web.webNativeMessagingExtensionAbility

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @csliutt-private-->
<!--Designer: @ringking0-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=297099253904002b9622394855cd624fb1a1072a translatedAt=2026-08-03T09:41:35.388Z pushedAt=2026-08-07T10:50:45.359Z -->

WebNativeMessagingExtensionAbility is a base class for web native message communication extension provided by ArkWeb, inherited from ExtensionAbility. It allows web pages to establish a secure, bidirectional pipe communication channel with system native services through the Native Messaging mechanism. By inheriting this class and implementing its lifecycle callbacks (such as [onConnectNative](#onconnectnative), [onDisconnectNative](#ondisconnectnative), and [onDestroy](#ondestroy)), developers can detect connection establishment when a web page initiates a connection request, obtain the caller identity and bidirectional pipe file descriptors (see [ConnectionInfo](#connectioninfo)), and release resources when the connection is disconnected or the extension is destroyed. This capability is primarily used in scenarios where browser extensions communicate with apps, enabling efficient message passing and data exchange to enhance extension integration and functionality. The app side must manage pipe read/write operations, permission verification, and the Ability lifecycle on its own.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { WebNativeMessagingExtensionAbility } from '@kit.ArkWeb';
```

## WebNativeMessagingExtensionAbility

Provides the web native messaging capability and is inherited from ExtensionAbility.

### Attributes

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| ------ | ------ | ------ | ------ | ------ |
| context | [WebNativeMessagingExtensionContext](arkts-apis-web-webNativeMessagingExtensionContext.md) | No | No | Context of the current web native message ExtensionAbility. |

### onConnectNative

onConnectNative(info: ConnectionInfo): void

Called when a web native message connection is established. In this callback, you can obtain the connection information for subsequent message communication processing.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ---- | ------ |
| info | [ConnectionInfo](#connectioninfo) | Yes| Connection information.|

**Example**

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onConnectNative(info: ConnectionInfo): void {
    console.info('Web Native connection established!');
    console.info(`Connection ID: ${info.connectionId}`);
    console.info(`Caller bundle: ${info.bundleName}`);
    // Process the service logic after the connection is established.
  }
}
```

### onDisconnectNative

onDisconnectNative(info: ConnectionInfo): void

Called when a web native message connection is disconnected. In this callback, you can release resources related to the connection and complete necessary cleanup.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ---- | ------ |
| info | [ConnectionInfo](#connectioninfo) | Yes| Connection information.|

**Example**

```ts
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onDisconnectNative(info: ConnectionInfo): void {
    console.info('Web Native connection closed!');
    console.info(`Connection ID: ${info.connectionId}`);
    // Process the cleanup after the connection is disconnected.
  }
}
```

### onDestroy

onDestroy(): void

Called when the WebNativeMessagingExtensionAbility is destroyed. In this callback, you can release all occupied resources and complete final cleanup operations.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Example**

```ts
import { WebNativeMessagingExtensionAbility } from '@kit.ArkWeb';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onDestroy(): void {
    console.info('WebNativeMessagingExtensionAbility is about to be destroyed!');
    // Release resources or perform cleanup operations.
  }
}
```

## ConnectionInfo

Represents the information object of the web native messaging connection.

**System capability**: SystemCapability.Web.Webview.Core

| Name| Type| Read-Only| Optional| Description|
| ------ | ------ | ------ | ------ | ------ |
| connectionId | number | No | No | Unique identifier of the connection, used to distinguish and manage different Web native message connections. It can be used to locate a specific connection during logging, status tracking, or resource cleanup. |
| bundleName | string | No | No | App package name of the caller, used for identity identification and permission verification. It can be used to determine whether to allow the app to establish a connection or perform message interaction. |
| extensionOrigin | string | No | No | Original URL of the caller extension, used for security control and origin identification. It can be used to determine the legitimacy of the extension or implement domain-based access policies. |
| fdRead | number | No | No | Pipe file descriptor used for reading data. Messages can be read from the Web side through this file descriptor. |
| fdWrite | number | No | No | Pipe file descriptor used for writing data. Messages can be sent to the Web side through this file descriptor. |