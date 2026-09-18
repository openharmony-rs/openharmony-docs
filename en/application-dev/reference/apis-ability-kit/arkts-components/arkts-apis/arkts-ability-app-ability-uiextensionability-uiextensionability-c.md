# UIExtensionAbility

UIExtensionAbility is an ExtensionAbility component with a User Interface (UI). It inherits from [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md) and provides basic lifecycle capabilities such as component creation, destruction, and foreground/background switching. Unlike the UIAbility, the UIExtensionAbility does not appear as a separate mission in the mission view. The foreground/background state and visibility of the UIExtensionAbility follow those of its host window. You cannot directly inherit from the UIExtensionAbility. However, you can choose other components that inherit from UIExtensionAbility based on specific service scenarios. For example, when handling data shared from other applications, you can use the [ShareExtensionAbility](arkts-ability-app-ability-shareextensionability-shareextensionability-c.md); when providing widget editing functionality, you can use the [FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability-formeditextensionability-c.md). For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship).

**Inheritance/Implementation:** UIExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { UIExtensionAbility } from '@kit.AbilityKit';
```

## onBackground

```TypeScript
onBackground(): void
```

Called when a UIExtensionAbility transitions from the foreground to the background. You can release resources when the UI is no longer invisible within this callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

```TypeScript
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { ShareExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onBackground() {
    console.info(TAG, `onBackground`);
  }
}
```

## onCreate

```TypeScript
onCreate(launchParam: AbilityConstant.LaunchParam): void
```

Called when a UIExtensionAbility instance is created. You can execute initialization logic (such as defining variables and loading resources) within this callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| launchParam | [AbilityConstant.LaunchParam](arkts-ability-abilityconstant-launchparam-i.md) | Yes | Parameters for application launch, including the reason for application launch and the reason for the last application exit.<br>**Since:** 12 |

**Examples**

```TypeScript
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { ShareExtensionAbility, AbilityConstant } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onCreate(launchParam: AbilityConstant.LaunchParam) {
    console.info(TAG, `onCreate, launchParam: ${JSON.stringify(launchParam)}`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

Called when a UIExtensionAbility is destroyed. You can clear resources and save data during this lifecycle. This API returns the result synchronously or uses a promise to return the result. After the **onDestroy()** lifecycle callback is executed, the application may exit. Consequently, the asynchronous function (for example, asynchronously writing data to the database) in **onDestroy()** may fail to be executed. Using a Promise for asynchronous callback is recommended to prevent such issues.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
A synchronous callback example is as follows:
```

```TypeScript
An asynchronous callback example is as follows:
```

## onForeground

```TypeScript
onForeground(): void
```

Called when a UIExtensionAbility is initially launched into the foreground or transitions from the background to the foreground. You can apply for resources when the UI becomes visible within this callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

```TypeScript
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { ShareExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onForeground() {
    console.info(TAG, `onForeground`);
  }
}
```

## onSessionCreate

```TypeScript
onSessionCreate(want: Want, session: UIExtensionContentSession): void
```

Called when a [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) instance is created. You can load a page through the UIExtensionContentSession instance within this callback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Data passed by the caller when launching the UIExtensionAbility. |
| session | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance. |

**Examples**

```TypeScript
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { ShareExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
    try {
      session.loadContent('pages/Index');
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`Failed to load content, code: ${code}, msg: ${message}`);
    }
  }
}
```

## onSessionDestroy

```TypeScript
onSessionDestroy(session: UIExtensionContentSession): void
```

Called when a UIExtensionContentSession is destroyed. It informs applications that the UIExtensionContentSession instance is no longer available for use.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance. |

**Examples**

```TypeScript
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { ShareExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

const TAG: string = '[testTag] ShareExtAbility';

export default class ShareExtAbility extends ShareExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    console.info(TAG, `onSessionDestroy`);
  }
}
```

## context

```TypeScript
context: UIExtensionContext
```

Context of the UIExtensionAbility.

**Type:** [UIExtensionContext](arkts-ability-uiextensioncontext-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
