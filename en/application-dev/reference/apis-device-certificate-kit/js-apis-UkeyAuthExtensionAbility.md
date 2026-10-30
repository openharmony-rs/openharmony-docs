# @ohos.security.UkeyAuthExtensionAbility (UKey Authentication Extension Capability)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=4c527713007118f6425722eade659066f086fae1 translatedAt=2026-10-30T06:44:01.588Z pushedAt=2026-10-30T09:23:25.816Z nl=1 -->

**UkeyAuthExtensionAbility** is an ExtensionAbility component used for UKey authentication UI display, which inherits from [ExtensionAbility](../apis-ability-kit/js-apis-app-ability-extensionAbility.md). Driver vendors can provide a custom UKey authentication UI by inheriting **UkeyAuthExtensionAbility** and implementing the related lifecycle callbacks. The UI is displayed through the [UIExtensionContentSession](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md) started by the host application.

Unlike [UIExtensionAbility](../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md), **UkeyAuthExtensionAbility** does not provide the **onForeground** and **onBackground** lifecycle callbacks. Only apps granted the **ohos.permission.START_SYSTEM_DIALOG** permission can start **UkeyAuthExtensionAbility**.

**Since:** 26.0.1

## Modules to Import

```ts
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## UkeyAuthExtensionAbility

Represents the UKey authentication UI extension component, which provides lifecycle callbacks such as component creation, session creation, session destruction, and component destruction.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

### Attributes

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog
 
**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| context | [UkeyAuthExtensionContext](js-apis-UkeyAuthExtensionContext.md) | No | No | Context of the **UkeyAuthExtensionAbility**. |

### onCreate

onCreate(launchParam: AbilityConstant.LaunchParam): void

Defines a callback invoked when the **UkeyAuthExtensionAbility** component instance is created. You can perform initialization logic in this callback, such as defining variables and loading resources.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| launchParam | [AbilityConstant.LaunchParam](../apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam) | Yes | Parameters for app launch, including the reason for app launch and the reason for the last app exit. |

**Example**

```ts
import { AbilityConstant } from '@kit.AbilityKit';
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onCreate(launchParam: AbilityConstant.LaunchParam): void {
    console.info('UkeyAuthExtension onCreate');
  }
}
```

### onSessionCreate

onSessionCreate(want: Want, session: UIExtensionContentSession): void

Defines a callback invoked after the [UIExtensionContentSession](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md) instance is created. You can load a page through the **UIExtensionContentSession** instance in this callback.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Data passed by the caller when starting the **UkeyAuthExtensionAbility**. |
| session | [UIExtensionContentSession](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md) | Yes | **UIExtensionContentSession** instance. |

**Example**

```ts
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    console.info('UkeyAuthExtension onSessionCreate');
    session.loadContent('pages/AuthPage');
  }
}
```

### onSessionDestroy

onSessionDestroy(session: UIExtensionContentSession): void

 Defines a callback invoked when the [UIExtensionContentSession](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md) instance is destroyed. This callback notifies you that the **UIExtensionContentSession** instance has been destroyed and can no longer be used.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| session | [UIExtensionContentSession](../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md) | Yes | **UIExtensionContentSession** instance. |

**Example**

```ts
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession): void {
    console.info('UkeyAuthExtension onSessionDestroy');
  }
}
```

### onDestroy

onDestroy(): void | Promise\<void>

Defines a callback invoked when the **UkeyAuthExtensionAbility** component is destroyed. You can perform operations such as resource cleanup and data saving in this lifecycle. This API uses a synchronous callback or a promise to return the result.

After the **onDestroy** lifecycle callback is executed, the app may exit. Consequently, the asynchronous function (for example, asynchronously writing data to the database) in **onDestroy()** may fail to be executed. It is recommended to use a promise to return the result to prevent asynchronous functions in **onDestroy** (for example, asynchronously writing data to the database) from failing to be executed correctly due to app exit.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| void \| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onDestroy(): void | Promise<void> {
    console.info('UkeyAuthExtension onDestroy');
    return new Promise<void>((resolve) => {
      resolve(undefined);
    });
  }
}
```