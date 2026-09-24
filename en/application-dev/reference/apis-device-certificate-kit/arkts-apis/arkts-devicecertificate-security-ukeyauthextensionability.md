# @ohos.security.UkeyAuthExtensionAbility

## Modules to Import

```TypeScript
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [UkeyAuthExtensionAbility](arkts-devicecertificate-security-ukeyauthextensionability-ukeyauthextensionability-c.md) | UkeyAuthExtensionAbility is an ExtensionAbility component for UKey authentication UI display. It inherits from [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md). You can implement this class to provide UKey authentication UI. The UI of a UkeyAuthExtensionAbility is displayed through a [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) started by the host application. Unlike the UIExtensionAbility, the UkeyAuthExtensionAbility does not provide onForeground and onBackground lifecycle callbacks. Only applications granted ohos.permission.START_SYSTEM_DIALOG can start it. |
