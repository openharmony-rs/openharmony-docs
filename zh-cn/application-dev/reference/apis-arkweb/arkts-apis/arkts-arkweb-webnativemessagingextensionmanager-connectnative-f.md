# connectNative

## 导入模块

```TypeScript
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
```

## connectNative

```TypeScript
function connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): number
```

将当前Ability连接到指定的Web原生消息扩展Ability。

**起始版本：** 21

**需要权限：** ohos.permission.WEB_NATIVE_MESSAGING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-webNativeMessagingExtensionManager-function connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): number--><!--Device-webNativeMessagingExtensionManager-function connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | 是 | 调用方UIAbility的上下文。 |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的want信息，其parameters中需包含'ohos.arkweb.messageReadPipe'（读管道FD）、' ohos.arkweb.messageWritePipe'（写管道FD）和'ohos.arkweb.extensionOrigin'（插件URI）。 |
| callback | [WebExtensionConnectionCallback](arkts-arkweb-webnativemessagingextensionmanager-webextensionconnectioncallback-i.md) | 是 | WebExtensionConnection状态的回调对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 连接的标识ID，由[connectNative]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

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

