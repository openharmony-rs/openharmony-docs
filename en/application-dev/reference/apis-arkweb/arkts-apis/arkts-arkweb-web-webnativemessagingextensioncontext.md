# @ohos.web.WebNativeMessagingExtensionContext

## Modules to Import

```TypeScript
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [WebNativeMessagingExtensionContext](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md) | WebNativeMessagingExtensionContext is the runtime context of the native web message extension ([WebNativeMessagingExtensionAbility](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md)). It inherits from ExtensionContext and provides lifecycle management, ability startup, and native message connection control capabilities for the extension ability. In an extension that inherits from WebNativeMessagingExtensionAbility, developers can obtain this context through `this.context` and then call [startAbility](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#startability) to start another ability, call [startAbilityForResult](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#startabilityforresult) to start a UIAbility and receive the return result, call [terminateSelf](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#terminateself) to terminate the current extension, or call [stopNativeConnection](arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md#stopnativeconnection) to stop a specified native web message connection. |
