# UkeyAuthExtensionAbility

```TypeScript
declare class UkeyAuthExtensionAbility extends ExtensionAbility
```

UkeyAuthExtensionAbility is an ExtensionAbility component for UKey authentication UI display. It inherits from [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md). You can implement this class to provide UKey authentication UI. The UI of a UkeyAuthExtensionAbility is displayed through a [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) started by the host application. Unlike the UIExtensionAbility, the UkeyAuthExtensionAbility does not provide onForeground and onBackground lifecycle callbacks. Only applications granted ohos.permission.START_SYSTEM_DIALOG can start it.

**Inheritance/Implementation:** UkeyAuthExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 26.0.1

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## onCreate

```TypeScript
onCreate(launchParam: AbilityConstant.LaunchParam): void
```

Called when a UkeyAuthExtensionAbility instance is created. You can execute initialization logic (such as defining variables and loading resources) within this callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| launchParam | [AbilityConstant.LaunchParam](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-launchparam-i.md) | Yes | Parameters for application launch, including the reason for application launch and the reason for the last application exit. |

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

Called when a UkeyAuthExtensionAbility is destroyed. You can clear resources and save data during this lifecycle. This API returns the result synchronously or uses a promise to return the result. After the **onDestroy()** lifecycle callback is executed, the application may exit. Consequently, the asynchronous function (for example, asynchronously writing data to the database) in **onDestroy()** may fail to be executed. Using a Promise for asynchronous callback is recommended to prevent such issues.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## onSessionCreate

```TypeScript
onSessionCreate(want: Want, session: UIExtensionContentSession): void
```

Called when a UIExtensionContentSession instance is created. You can load a page through the UIExtensionContentSession instance within this callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Data passed by the caller when launching the UkeyAuthExtensionAbility. |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance. |

## onSessionDestroy

```TypeScript
onSessionDestroy(session: UIExtensionContentSession): void
```

Called when a UIExtensionContentSession is destroyed. It informs applications that the UIExtensionContentSession instance is no longer available for use.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance. |

## context

```TypeScript
context: UkeyAuthExtensionContext
```

Context of the UkeyAuthExtensionAbility.

**Type:** [UkeyAuthExtensionContext](arkts-devicecertificate-security-ukeyauthextensioncontext-ukeyauthextensioncontext-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog
