# @ohos.web.webNativeMessagingExtensionManager

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @csliutt-private-->
<!--Designer: @ringking0-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9c41f9fad7f6d910dff2a356347531b943719c3e translatedAt=2026-08-03T09:46:29.780Z pushedAt=2026-08-07T10:53:39.596Z -->

The webNativeMessagingExtensionManager module is a Web native message extension management module provided by ArkWeb. It is used to initiate and manage connections from the app side (caller) to [WebNativeMessagingExtensionAbility](./arkts-apis-web-webNativeMessagingExtensionAbility.md). Developers can call [connectNative](#webnativemessagingextensionmanagerconnectnative) to specify the target extension Ability and establish a connection, use the returned connection ID and [WebExtensionConnectionCallback](#webextensionconnectioncallback) to listen for connection establishment, disconnection, and failure events, and call [disconnectNative](#webnativemessagingextensionmanagerdisconnectnative) to actively release the connection. This module is suitable for scenarios where browser extensions communicate with apps. Before using it, you need to request the [ohos.permission.WEB_NATIVE_MESSAGING](../../security/AccessToken/restricted-permissions.md#ohospermissionweb_native_messaging) permission, and it is available only under the Stage model.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
```

## ConnectionNativeInfo

Represents the information about the web native message connection.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| connectionId | number | No | No | Unique identifier of the Web native message extension connection, returned by connectNative() and used to identify and manage the connection. |
| bundleName | string | No| No| Bundle name of the web native message extension application.|
| extensionOrigin | string | No| No| Source URL of the browser extension.|
| extensionPid | number | No| No| Process ID of the web native message extension.|

## NmErrorCode

Provides the native messaging error codes.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| PERMISSION_DENY | 17100203 | Permission denied due to missing ohos.permission.WEB_NATIVE_MESSAGING. |
| WANT_CONTENT_ERROR | 17100202 | The Want content is invalid. |
| INNER_ERROR | 17100201 | An internal error has occurred. |

## WebExtensionConnectionCallback

### onConnect

onConnect(connection: ConnectionNativeInfo): void

Called when a connection is set up.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| connection | [ConnectionNativeInfo](#connectionnativeinfo) | Yes | Connection information, including the connection ID, extension application bundle name, browser extension source URL, and extension process ID. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // Obtain UIAbilityContext.
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // Extension URI required here.
          },
        };

        let callback: webNativeMessagingExtensionManager.WebExtensionConnectionCallback = {
            onConnect(connection) {
                console.info('onConnect, connectionId:' + connection.connectionId);
            },
            onDisconnect(connection) {
                console.info('onDisconnect');
            },
            onFailed(code, errMsg) {
                console.info(`onFailed, code:${code} errMsg:${errMsg}`);
            }
        };

        let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### onDisconnect

onDisconnect(connection: ConnectionNativeInfo): void

Called when a connection is interrupted.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| connection | [ConnectionNativeInfo](#connectionnativeinfo) | Yes | Connection information, including the connection ID, extension application package name, browser extension source URL, and extension process ID. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // Obtain UIAbilityContext.
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // The extension URI is required here.
          },
        };

        let callback: webNativeMessagingExtensionManager.WebExtensionConnectionCallback = {
            onConnect(connection) {
                console.info('onConnect, connectionId:' + connection.connectionId);
            },
            onDisconnect(connection) {
                console.info('onDisconnect');
            },
            onFailed(code, errMsg) {
                console.info(`onFailed, code:${code} errMsg:${errMsg}`);
            }
        };

        let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### onFailed

onFailed(code: NmErrorCode, errMsg: string): void

Called when the connection fails.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| code | [NmErrorCode](#nmerrorcode) | Yes| Error code.|
| errMsg | string | Yes| Error message.|

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // Obtain UIAbilityContext.
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // Enter the extension URI here.
          },
        };

        let callback: webNativeMessagingExtensionManager.WebExtensionConnectionCallback = {
            onConnect(connection) {
                console.info('onConnect, connectionId:' + connection.connectionId);
            },
            onDisconnect(connection) {
                console.info('onDisconnect');
            },
            onFailed(code, errMsg) {
                console.info(`onFailed, code:${code} errMsg:${errMsg}`);
            }
        };

        let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## webNativeMessagingExtensionManager.connectNative

connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): number

Connects the current ability to the specified web native message extension ability.

**Required permissions**: ohos.permission.WEB_NATIVE_MESSAGING

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Context of the calling UIAbility. |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Want information for starting the Ability, whose parameters must include 'ohos.arkweb.messageReadPipe' (read pipe FD), 'ohos.arkweb.messageWritePipe' (write pipe FD), and 'ohos.arkweb.extensionOrigin' (extension URI). |
| callback | [WebExtensionConnectionCallback](#webextensionconnectioncallback) | Yes| Callback object of the WebExtensionConnection status.|

**Return value**

| Type| Description|
|------|------|
| number | ID of the connection, returned by the [connectNative](#webnativemessagingextensionmanagerconnectnative) method, used to uniquely identify a Web native message extension connection. The connection must be released through disconnectNative after being established. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
|----------|----------|
| 801 | Capability not supported. |

**Example**

```ts
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // Obtain UIAbilityContext.
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // The plugin URI is required here.
          },
        };

        let callback: webNativeMessagingExtensionManager.WebExtensionConnectionCallback = {
            onConnect(connection) {
                console.info('onConnect, connectionId:' + connection.connectionId);
            },
            onDisconnect(connection) {
                console.info('onDisconnect');
            },
            onFailed(code, errMsg) {
                console.info(`onFailed, code:${code} errMsg:${errMsg}`);
            }
        };

        let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## webNativeMessagingExtensionManager.disconnectNative

disconnectNative(connectionId: number): Promise&lt;void&gt;

Disconnects the connection of a specified web native message extension.

**Required permissions**: ohos.permission.WEB_NATIVE_MESSAGING

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| connectionId | number | Yes | Connection identifier, used to identify a Web native message extension connection, returned by the [connectNative](#webnativemessagingextensionmanagerconnectnative) method. After establishing the connection, it must be released through disconnectNative. A valid connection ID returned by connectNative must be used. |

**Return value**

| Type| Description|
|------|------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
|----------|----------|
| 201 | Permission verification failed. |
| 801 | Capability not supported. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';

export default class EntryAbility extends UIAbility {
  async disconnect() {
    try {
        let connectionId = 1;
        // Assume that the connection has been established and connectionId has been obtained.
        await webNativeMessagingExtensionManager.disconnectNative(connectionId).then(() => {
            console.info('disconnectNative success');
        })
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectNative failed, code is ${code}, message is ${message}`);
    }
  }
  onForeground() {
    this.disconnect();
  }
}
```