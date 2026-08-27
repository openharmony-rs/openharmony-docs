# WebNativeMessagingExtensionAbility

为开发者提供Web原生消息通信能力，继承自ExtensionAbility。

**继承/实现关系：** WebNativeMessagingExtensionAbility extends ExtensionAbility

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
```

## onConnectNative

```TypeScript
onConnectNative(info: ConnectionInfo): void
```

Web原生消息连接建立时回调此方法。在此回调中，可以获取连接信息，用于后续的消息通信处理。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ConnectionInfo](arkts-arkweb-web-webnativemessagingextensionability-connectioninfo-i.md) | 是 | 连接信息对象。 |

**示例**

```TypeScript
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onConnectNative(info: ConnectionInfo): void {
    console.info('Web Native connection established!');
    console.info(`Connection ID: ${info.connectionId}`);
    console.info(`Caller bundle: ${info.bundleName}`);
    // 在此处处理连接建立后的业务逻辑
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

WebNativeMessagingExtensionAbility销毁时回调。在此回调中，可以释放所有占用的资源，并完成最终的清理操作。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

```TypeScript
import { WebNativeMessagingExtensionAbility } from '@kit.ArkWeb';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onDestroy(): void {
    console.info('WebNativeMessagingExtensionAbility is about to be destroyed!');
    // 在此处释放资源或者执行清理操作
  }
}
```

## onDisconnectNative

```TypeScript
onDisconnectNative(info: ConnectionInfo): void
```

Web原生消息连接断开时回调此方法。在此回调中，可以释放与该连接相关的资源，并完成必要的清理工作。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ConnectionInfo](arkts-arkweb-web-webnativemessagingextensionability-connectioninfo-i.md) | 是 | 连接信息对象。 |

**示例**

```TypeScript
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';

export class MyWebNativeMessagingExtension extends WebNativeMessagingExtensionAbility {
  onDisconnectNative(info: ConnectionInfo): void {
    console.info('Web Native connection closed!');
    console.info(`Connection ID: ${info.connectionId}`);
    // 在此处处理连接断开后的清理工作
  }
}
```

## context

```TypeScript
context: WebNativeMessagingExtensionContext
```

当前Web原生消息扩展Ability的上下文。

**类型：** [WebNativeMessagingExtensionContext](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md)

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core
