# EmbeddedComponent

**EmbeddedComponent** is used to embed, in the current page, the UI provided by an [EmbeddedUIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddeduiextensionability-embeddeduiextensionability-c.md) within the same app or from another app that meets cross-application permission conditions. The **EmbeddedUIExtensionAbility** runs in an independent process, handling page layout and rendering.

It is usually used in modular development scenarios where process isolation is required.

> **NOTE:** 

## Constraints

The **EmbeddedComponent** is supported only on devices configured with multi-process permissions. Developers can use the **canIUse** API or check system settings to determine whether the current device supports multi-process permissions.

**EmbeddedComponent** can only be used in a **UIAbility**, and by default, the launched **EmbeddedUIExtensionAbility** must belong to the same app as the **UIAbility**. Since API version 26.0.0, cross-application launching of the **EmbeddedUIExtensionAbility** by the **EmbeddedComponent** is allowed when all of the following conditions are met:

- The app to which the **EmbeddedComponent** belongs has applied for the  
**ohos.permission.SUPPORT_CROSS_APP_EMBED_FOR_OA** permission (this permission can only be applied for by enterprise normal apps).

- The appIdentifier of the app is in the allowlist of apps supported by the **EmbeddedUIExtensionAbility** (that is,  
the **appIdentifierAllowList** attribute of the extensionAbilities tag).

## Child Components

Not supported

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
  loader: import('../api/@ohos.app.ability.Want').default,
  type: EmbeddedType
)
```

Creates a cross-process embedded component to display the UI of the **EmbeddedUIExtensionAbility** with the same bundle name or that meets cross-application permission conditions.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmbeddedComponentInterface-(  loader: import('../api/@ohos.app.ability.Want').default,  type: EmbeddedType): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentInterface-(  loader: import('../api/@ohos.app.ability.Want').default,  type: EmbeddedType): EmbeddedComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | Yes | **EmbeddedUIExtensionAbility** to be loaded. |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | Yes | Type of the provider. Currently, the supported value is [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md).EMBEDDED_UI_EXTENSION, indicating that the embedded UI is provided by **EmbeddedUIExtensionAbility**. |

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
  loader: import('../api/@ohos.app.ability.Want').default,
  type: EmbeddedType,
  options?: EmbeddedOptions
)
```

Creates a cross-process embedded component to display the UI of the **EmbeddedUIExtensionAbility** with the same bundle name or that meets cross-application permission conditions. Compared with the API in API version 12, this API adds the **options** parameter for passing construction parameters.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedComponentInterface-(  loader: import('../api/@ohos.app.ability.Want').default,  type: EmbeddedType,  options?: EmbeddedOptions): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentInterface-(  loader: import('../api/@ohos.app.ability.Want').default,  type: EmbeddedType,  options?: EmbeddedOptions): EmbeddedComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | Yes | **EmbeddedUIExtensionAbility** to load. |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | Yes | Type of the provider. The currently supported value is [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md).EMBEDDED_UI_EXTENSION, indicating that the embedded UI is provided by an **EmbeddedUIExtensionAbility**. |
| options | [EmbeddedOptions](arkts-arkui-embeddedcomponent-comp-embeddedoptions-i.md) | No | Optional configuration for the embedded component, used to set the placeholder, DPI follow strategy, window mode follow strategy, and more. For details, see [EmbeddedOptions](arkts-arkui-embeddedcomponent-comp-embeddedoptions-i.md). |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [EmbeddedOptions](arkts-arkui-embeddedcomponent-comp-embeddedoptions-i.md) | Used to pass optional construction parameters when creating an **EmbeddedComponent**. |
| [TerminationInfo](arkts-arkui-embeddedcomponent-comp-terminationinfo-i.md) | Provides the result returned by the started **EmbeddedUIExtensionAbility**. |

### Enums

| Name | Description |
| --- | --- |
| [EmbeddedDpiFollowStrategy](arkts-arkui-embeddedcomponent-comp-embeddeddpifollowstrategy-e.md) | Defines the DPI follow strategy, which is used to set the DPI to follow either the host or the **EmbeddedUIExtensionAbility**. For example, when the **EmbeddedUIExtensionAbility** needs to maintain visual consistency with the host app, you can choose to follow the host DPI. When the **EmbeddedUIExtensionAbility** needs to independently adapt to the DPI configuration of its own resources, you can choose to follow the **EmbeddedUIExtensionAbility** DPI. |
| [EmbeddedWindowModeFollowStrategy](arkts-arkui-embeddedcomponent-comp-embeddedwindowmodefollowstrategy-e.md) | Defines the window mode follow strategy, which is used to set the window mode to follow either the host or the **EmbeddedUIExtensionAbility**. For example, when the **EmbeddedUIExtensionAbility** needs to maintain the same window mode (such as full screen or split screen) as the host app, you can choose to follow the host. When the **EmbeddedUIExtensionAbility** needs to independently control the window mode, you can choose to follow the **EmbeddedUIExtensionAbility**. |
