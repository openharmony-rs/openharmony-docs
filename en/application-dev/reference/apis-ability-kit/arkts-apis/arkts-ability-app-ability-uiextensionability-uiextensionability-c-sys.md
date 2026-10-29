# UIExtensionAbility (System API)

```TypeScript
declare class UIExtensionAbility extends ExtensionAbility
```

UIExtensionAbility is an ExtensionAbility component with a User Interface (UI). It inherits from [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md) and provides basic lifecycle capabilities such as component creation, destruction, and foreground/background switching. Unlike the UIAbility, the UIExtensionAbility does not appear as a separate mission in the mission view. The foreground/background state and visibility of the UIExtensionAbility follow those of its host window. You cannot directly inherit from the UIExtensionAbility. However, you can choose other components that inherit from UIExtensionAbility based on specific service scenarios. For example, when handling data shared from other applications, you can use the [ShareExtensionAbility](arkts-ability-app-ability-shareextensionability-shareextensionability-c.md); when providing widget editing functionality, you can use the [FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability-formeditextensionability-c.md). For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship).

**Inheritance/Implementation:** UIExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 10

<!--Device-unnamed-declare class UIExtensionAbility extends ExtensionAbility--><!--Device-unnamed-declare class UIExtensionAbility extends ExtensionAbility-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { UIExtensionAbility } from '@kit.AbilityKit';
import { ConfigurationStrategy } from '@kit.AbilityKit';
```

## onGetConfigurationStrategy

```TypeScript
onGetConfigurationStrategy?: OnGetConfigurationStrategyFn
```

Called back to return the configuration strategy of the UIExtensionAbility. It is called after [onCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#oncreate) and before [onSessionCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onsessioncreate).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionAbility-onGetConfigurationStrategy?: OnGetConfigurationStrategyFn--><!--Device-UIExtensionAbility-onGetConfigurationStrategy?: OnGetConfigurationStrategyFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
