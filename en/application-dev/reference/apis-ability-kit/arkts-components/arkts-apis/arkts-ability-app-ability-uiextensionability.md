# @ohos.app.ability.UIExtensionAbility(ExtensionAbility with UI)

## Modules to Import

```TypeScript
import { UIExtensionAbility } from '@kit.AbilityKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) | UIExtensionAbility is an ExtensionAbility component with a User Interface (UI). It inherits from [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md) and provides basic lifecycle capabilities such as component creation, destruction, and foreground/background switching. Unlike the UIAbility, the UIExtensionAbility does not appear as a separate mission in the mission view. The foreground/background state and visibility of the UIExtensionAbility follow those of its host window. You cannot directly inherit from the UIExtensionAbility. However, you can choose other components that inherit from UIExtensionAbility based on specific service scenarios. For example, when handling data shared from other applications, you can use the [ShareExtensionAbility](arkts-ability-app-ability-shareextensionability-shareextensionability-c.md); when providing widget editing functionality, you can use the [FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability-formeditextensionability-c.md). For details about the inheritance relationship of each ability, see [Inheritance Relationship](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability-inheritance-relationship). |
