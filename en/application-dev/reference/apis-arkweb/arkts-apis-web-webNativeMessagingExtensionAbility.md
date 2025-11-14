# @ohos.web.WebNativeMessagingExtensionAbility (Web Native Messaging Extension Ability)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @weixin_41848015-->
<!--Designer: @libing23232323-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

WebNativeMessagingExtensionAbility provides the web native messaging capability and is inherited from ExtensionAbility.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import WebNativeMessagingExtensionAbility from '@kit.ArkWeb';
```

## WebNativeMessagingExtensionAbility

Provides the web native messaging capability and is inherited from ExtensionAbility.

### Attributes

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| ------ | ------ | ------ | ------ | ------ |
| context | [WebNativeMessagingExtensionContext](arkts-apis-web-webNativeMessagingExtensionContext.md) | No| No| Context of web native messaging.|

### onConnectNative

onConnectNative(info: ConnectionInfo): void

Called when a web native messaging connection is established.

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
    console.info(`Connnection ID: ${info.connectionId}`);
    console.info(`Caller bundle: ${info.bundleName}`);
    // Process the service logic after the connection is established.
  }
}
```

### onDisconnectNative

onDisconnectNative(info: ConnectionInfo): void

Called when a web native messaging connection is disconnected.

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
    console.info(`Connnection ID: ${info.connectionId}`);
    // Process the cleanup after the connection is disconnected.
  }
}
```

### onDestroy

onDestroy(): void

Called when the WebNativeMessagingExtensionAbility is destroyed.

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
| connectionId | number | No| No| Connection ID.|
| bundleName | string | No| No| Application bundle name of the caller.|
| extensionOrigin | string | No| No| Original URL of the caller extension.|
| fdRead | number | No| No| Pipe file descriptor used to read data.|
| fdWrite | number | No| No| Pipe file descriptor used to write data.|
