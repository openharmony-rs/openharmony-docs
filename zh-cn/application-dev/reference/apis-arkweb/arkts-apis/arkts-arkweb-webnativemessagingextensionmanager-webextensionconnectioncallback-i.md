# WebExtensionConnectionCallback

作为连接网络原生消息扩展时的输入参数，它用于接收连接期间的状态变化。

**起始版本：** 21

<!--Device-webNativeMessagingExtensionManager-interface WebExtensionConnectionCallback--><!--Device-webNativeMessagingExtensionManager-interface WebExtensionConnectionCallback-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
```

## onConnect

```TypeScript
onConnect(connection: ConnectionNativeInfo): void
```

建立连接时的回调函数。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebExtensionConnectionCallback-onConnect(connection: ConnectionNativeInfo): void--><!--Device-WebExtensionConnectionCallback-onConnect(connection: ConnectionNativeInfo): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | [ConnectionNativeInfo](arkts-arkweb-webnativemessagingextensionmanager-connectionnativeinfo-i.md) | 是 | 连接信息，包含连接ID、扩展应用包名、浏览器扩展源URL和扩展进程ID等信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // 获取UIAbilityContext
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, //假设此处为合法pipefd
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, //假设此处为合法pipefd
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // 此处需要插件URI
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
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import UIAbility from '@ohos.app.ability.UIAbility';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base'
import webNativeMessagingExtensionManager from '@ohos.web.webNativeMessagingExtensionManager';
import common from '@ohos.app.ability.common';

class ConnectionCallback implements webNativeMessagingExtensionManager.WebExtensionConnectionCallback {
  constructor() {
  }

  onConnect(connection: webNativeMessagingExtensionManager.ConnectionNativeInfo): void {
    console.info('onConnect, connectionId:' + connection.connectionId);
  }

  onDisconnect(connection: webNativeMessagingExtensionManager.ConnectionNativeInfo): void {
    console.info('onDisconnect');
  }

  onFailed(code: webNativeMessagingExtensionManager.NmErrorCode, errMsg: string): void {
    console.info(`onFailed, code:${code} errMsg:${errMsg}`);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      let context: common.UIAbilityContext = this.context; // 获取UIAbilityContext
      let parameters = new Record<string, Object>();
      parameters.set("ohos.arkweb.messageReadPipe", "333") // 假设此处为合法pipefd
      parameters.set("ohos.arkweb.messageWritePipe", "444") // 假设此处为合法pipefd
      parameters.set("ohos.arkweb.extensionOrigin", "chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/") // 此处需要插件URI
      let want:Want = {
        bundleName: 'com.example.app',
        abilityName: 'MyWebNativeMessageExtAbility',
        parameters: parameters,
      };
      let callback : ConnectionCallback = new ConnectionCallback() ;
      let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err: BusinessError) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(connection: ConnectionNativeInfo): void
```

断开连接时的回调函数。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebExtensionConnectionCallback-onDisconnect(connection: ConnectionNativeInfo): void--><!--Device-WebExtensionConnectionCallback-onDisconnect(connection: ConnectionNativeInfo): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | [ConnectionNativeInfo](arkts-arkweb-webnativemessagingextensionmanager-connectionnativeinfo-i.md) | 是 | 连接信息，包含连接ID、扩展应用包名、浏览器扩展源URL和扩展进程ID等信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // 获取UIAbilityContext
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, //假设此处为合法pipefd
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, //假设此处为合法pipefd
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // 此处需要插件URI
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
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import UIAbility from '@ohos.app.ability.UIAbility';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base'
import webNativeMessagingExtensionManager from '@ohos.web.webNativeMessagingExtensionManager';
import common from '@ohos.app.ability.common';

class ConnectionCallback implements webNativeMessagingExtensionManager.WebExtensionConnectionCallback {
  constructor() {
  }

  onConnect(connection: webNativeMessagingExtensionManager.ConnectionNativeInfo): void {
    console.info('onConnect, connectionId:' + connection.connectionId);
  }

  onDisconnect(connection: webNativeMessagingExtensionManager.ConnectionNativeInfo): void {
    console.info('onDisconnect');
  }

  onFailed(code: webNativeMessagingExtensionManager.NmErrorCode, errMsg: string): void {
    console.info(`onFailed, code:${code} errMsg:${errMsg}`);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      let context: common.UIAbilityContext = this.context; // 获取UIAbilityContext
      let parameters = new Record<string, Object>();
      parameters.set("ohos.arkweb.messageReadPipe", "333") // 假设此处为合法pipefd
      parameters.set("ohos.arkweb.messageWritePipe", "444") // 假设此处为合法pipefd
      parameters.set("ohos.arkweb.extensionOrigin", "chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/") // 此处需要插件URI
      let want:Want = {
        bundleName: 'com.example.app',
        abilityName: 'MyWebNativeMessageExtAbility',
        parameters: parameters,
      };
      let callback : ConnectionCallback = new ConnectionCallback() ;
      let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err: BusinessError) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## onFailed

```TypeScript
onFailed(code: NmErrorCode, errMsg: string): void
```

连接失败时的回调函数。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebExtensionConnectionCallback-onFailed(code: NmErrorCode, errMsg: string): void--><!--Device-WebExtensionConnectionCallback-onFailed(code: NmErrorCode, errMsg: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | [NmErrorCode](arkts-arkweb-webnativemessagingextensionmanager-nmerrorcode-e.md) | 是 | 错误码。 |
| errMsg | string | 是 | 错误码对应信息。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
        let context: common.UIAbilityContext = this.context; // 获取UIAbilityContext
        let want: Want = {
          bundleName: 'com.example.app',
          abilityName: 'MyWebNativeMessageExtAbility',
          parameters: {
            'ohos.arkweb.messageReadPipe': { 'type': 'FD', 'value': 333 }, //假设此处为合法pipefd
            'ohos.arkweb.messageWritePipe': { 'type': 'FD', 'value': 444 }, //假设此处为合法pipefd
            'ohos.arkweb.extensionOrigin': 'chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/' // 此处需要插件URI
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
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import UIAbility from '@ohos.app.ability.UIAbility';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base'
import webNativeMessagingExtensionManager from '@ohos.web.webNativeMessagingExtensionManager';
import common from '@ohos.app.ability.common';

class ConnectionCallback implements webNativeMessagingExtensionManager.WebExtensionConnectionCallback {
  constructor() {
  }

  onConnect(connection: webNativeMessagingExtensionManager.ConnectionNativeInfo): void {
    console.info('onConnect, connectionId:' + connection.connectionId);
  }

  onDisconnect(connection: webNativeMessagingExtensionManager.ConnectionNativeInfo): void {
    console.info('onDisconnect');
  }

  onFailed(code: webNativeMessagingExtensionManager.NmErrorCode, errMsg: string): void {
    console.info(`onFailed, code:${code} errMsg:${errMsg}`);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      let context: common.UIAbilityContext = this.context; // 获取UIAbilityContext
      let parameters = new Record<string, Object>();
      parameters.set("ohos.arkweb.messageReadPipe", "333") // 假设此处为合法pipefd
      parameters.set("ohos.arkweb.messageWritePipe", "444") // 假设此处为合法pipefd
      parameters.set("ohos.arkweb.extensionOrigin", "chrome-extension://knldjmfmopnpolahpmmgbagdohdnhkik/") // 此处需要插件URI
      let want:Want = {
        bundleName: 'com.example.app',
        abilityName: 'MyWebNativeMessageExtAbility',
        parameters: parameters,
      };
      let callback : ConnectionCallback = new ConnectionCallback() ;
      let connectionId = webNativeMessagingExtensionManager.connectNative(context, want, callback);
    } catch (err: BusinessError) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectNative failed, code is ${code}, message is ${message}`);
    }
  }
}
```

