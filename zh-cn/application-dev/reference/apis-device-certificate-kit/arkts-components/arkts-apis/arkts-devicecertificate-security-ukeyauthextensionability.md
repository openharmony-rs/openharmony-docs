# @ohos.security.UkeyAuthExtensionAbility

## 导入模块

```TypeScript
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [UkeyAuthExtensionAbility](arkts-devicecertificate-security-ukeyauthextensionability-ukeyauthextensionability-c.md) | UkeyAuthExtensionAbility是用于UKey认证UI显示的ExtensionAbility组件。它继承自[ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)。您可以实现此类来提供UKey认证UI。UkeyAuthExtensionAbility的UI通过宿主应用启动的[UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md)进行显示。与UIExtensionAbility不同，UkeyAuthExtensionAbility不提供onForeground和onBackground生命周期回调。仅被授予ohos.permission.START_SYSTEM_DIALOG权限的应用可以启动它。 |
