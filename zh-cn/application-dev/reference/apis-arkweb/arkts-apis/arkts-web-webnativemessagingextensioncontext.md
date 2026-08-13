# @ohos.web.WebNativeMessagingExtensionContext

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [WebNativeMessagingExtensionContext](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md) | WebNativeMessagingExtensionContext是Web原生消息扩展（ [WebNativeMessagingExtensionAbility](../../apis-na/arkts-apis/arkts-na-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#WebNativeMessagingExtensionAbility)）的运行上下文，继承自ExtensionContext，为 扩展Ability提供生命周期管理、Ability启动以及原生消息连接控制能力。开发者可在继承WebNativeMessagingExtensionAbility的扩展中通过`this.context`获取该上下文，进而调用 [startAbility](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#startAbility)启动其他Ability、调用 [startAbilityForResult](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#startAbilityForResult)启动UIAbility并接收返回结果、调用 [terminateSelf](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#terminateSelf)结束当前扩展，或调用 [stopNativeConnection](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#stopNativeConnection)停止指定的Web原生消息连接。 > **说明:** > > 本模块接口仅可在Stage模型下使用。 |

