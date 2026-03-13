# @ohos.web.webNativeMessagingExtensionManager (Web Native Messaging Extension Manager)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @weixin_41848015-->
<!--Designer: @libing23232323-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

The webNativeMessagingExtensionManager module provides the capability of managing message extensions based on web standards.

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
| connectionId | number | No| No| Connection ID.|
| bundleName | string | No| No| Bundle name of the web native message extension application.|
| extensionOrigin | string | No| No| Source URL of the browser extension.|
| extensionPid | number | No| No| Process ID of the web native message extension.|

## NmErrorCode

Provides the native messaging error codes.

**System capability**: SystemCapability.Web.Webview.Core

| Name         | Value| Description                                     |
| ------------- | -- |----------------------------------------- |
| PERMISSION_DENY | 17100203 | Permission denied due to missing ohos.permission.WEB_NATIVE_MESSAGING. |
| WANT_CONTENT_ERROR | 17100202 | The want content is invalid. |
| INNER_ERROR | 17100201 | Inner error for native messaging.Error code: |

## WebExtensionConnectionCallback

### onConnect
onConnect(connection: ConnectionNativeInfo): void

Called when a connection is set up.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|------|------|------|------|
| connection | [ConnectionNativeInfo](#connectionnativeinfo) | Yes| Connection information.|

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
        let want:Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // The plug-in URI is required.
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
| connection | [ConnectionNativeInfo](#connectionnativeinfo) | Yes| Connection information.|

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
        let want:Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // The plug-in URI is required.
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
        let want:Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // The plug-in URI is required.
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
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes| Context of the web native message extension.|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| Want information about the target ability.|
| callback | [WebExtensionConnectionCallback](#webextensionconnectioncallback) | Yes| Callback object of the WebExtensionConnection status.|

**Return value**

| Type| Description|
|------|------|
| number | Connection ID.|

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
        let want:Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, // Assume that the pipefd is valid.
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, // Assume that the pipefd is valid.
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // The plug-in URI is required.
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
| connectionId | number | Yes| Connection ID.|

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
