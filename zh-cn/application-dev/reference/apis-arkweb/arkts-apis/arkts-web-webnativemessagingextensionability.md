# @ohos.web.WebNativeMessagingExtensionAbility

WebNativeMessagingExtensionAbility是ArkWeb提供的Web原生消息通信扩展基类，继承自ExtensionAbility（扩展能力基类），允许Web页面通过Native Messaging机制与系统原
 生服务建立安全、双向的管道通信通道。开发者通过继承该类并实现其生命周期回调（如[onConnectNative](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#onconnectnative)、
 [onDisconnectNative](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#ondisconnectnative)、
 [onDestroy](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#ondestroy)），可以在Web页面发起连接请求时感知连接建立、获取调用方身份与双向管道文件描述符（见
 [ConnectionInfo](arkts-arkweb-web-webnativemessagingextensionability-connectioninfo-i.md)），并在连接断开或扩展销毁时完成资源释放。该能力主要用于浏览器扩展与应用通信的场景，实现高效的消息传递和数据交换，提升扩展的集成度和功能性。应用侧需自行管理管
 道读写、权限校验及Ability生命周期。


## 导入模块

```TypeScript
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [WebNativeMessagingExtensionAbility](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md) | 为开发者提供Web原生消息通信能力，继承自ExtensionAbility。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectionInfo](arkts-arkweb-web-webnativemessagingextensionability-connectioninfo-i.md) | Web原生消息连接的信息对象。 |
