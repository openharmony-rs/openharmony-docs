# UkeyAuthExtensionAbility

```TypeScript
declare class UkeyAuthExtensionAbility extends ExtensionAbility
```

UkeyAuthExtensionAbility是用于UKey认证UI显示的ExtensionAbility组件。它继承自[ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)。您可以实现此类来提供UKey认证UI。UkeyAuthExtensionAbility的UI通过宿主应用启动的[UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md)进行显示。与UIExtensionAbility不同，UkeyAuthExtensionAbility不提供onForeground和onBackground生命周期回调。仅被授予ohos.permission.START_SYSTEM_DIALOG权限的应用可以启动它。

**继承/实现关系：** UkeyAuthExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## onCreate

```TypeScript
onCreate(launchParam: AbilityConstant.LaunchParam): void
```

当UkeyAuthExtensionAbility实例创建时调用。您可以在此回调中执行初始化逻辑（例如定义变量和加载资源）。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| launchParam | [AbilityConstant.LaunchParam](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-launchparam-i.md) | 是 | 应用启动参数，包括应用启动原因和上次应用退出原因。 |

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

当UkeyAuthExtensionAbility被销毁时调用。您可以在此生命周期中清除资源并保存数据。此API同步返回结果或使用Promise返回结果。**onDestroy()**生命周期回调执行后，应用可能退出。因此，**onDestroy()**中的异步函数（例如异步写入数据库）可能无法执行。建议使用Promise进行异步回调以避免此类问题。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## onSessionCreate

```TypeScript
onSessionCreate(want: Want, session: UIExtensionContentSession): void
```

当UIExtensionContentSession实例创建时调用。您可以在此回调中通过UIExtensionContentSession实例加载页面。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动UkeyAuthExtensionAbility时调用方传递的数据。 |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | 是 | UIExtensionContentSession实例。 |

## onSessionDestroy

```TypeScript
onSessionDestroy(session: UIExtensionContentSession): void
```

当UIExtensionContentSession被销毁时调用。它通知应用UIExtensionContentSession实例不再可用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | 是 | UIExtensionContentSession实例。 |

## context

```TypeScript
context: UkeyAuthExtensionContext
```

UkeyAuthExtensionAbility的上下文。

**类型：** [UkeyAuthExtensionContext](arkts-devicecertificate-security-ukeyauthextensioncontext-ukeyauthextensioncontext-c.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog
