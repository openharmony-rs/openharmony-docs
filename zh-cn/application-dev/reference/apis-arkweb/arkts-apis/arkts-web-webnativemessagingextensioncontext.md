# @ohos.web.WebNativeMessagingExtensionContext

## 导入模块

```TypeScript
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [WebNativeMessagingExtensionContext](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md) | WebNativeMessagingExtensionContext是Web原生消息扩展（ [WebNativeMessagingExtensionAbility](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md)）的运行上下文，继承自ExtensionContext，为 扩展Ability提供生命周期管理、Ability启动以及原生消息连接控制能力。开发者可在继承WebNativeMessagingExtensionAbility的扩展中通过`this.context`获取该上下文，进而调用 [startAbility](../../apis-na/arkts-apis/arkts-na-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#startability)启动其他Ability、调用 [startAbilityForResult](../../apis-na/arkts-apis/arkts-na-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#startabilityforresult)启动UIAbility并接收返回结果、调用 [terminateSelf](../../apis-na/arkts-apis/arkts-na-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#terminateself)结束当前扩展，或调用 [stopNativeConnection](../../apis-na/arkts-apis/arkts-na-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#stopnativeconnection)停止指定的Web原生消息连接。 > **说明:** > > 本模块接口仅可在Stage模型下使用。 |

