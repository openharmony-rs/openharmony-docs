# EmbeddedComponent

The **EmbeddedComponent** is a component used to embed into the current page the UI provided by another [EmbeddedUIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddeduiextensionability-embeddeduiextensionability-c.md) in the same application. The EmbeddedUIExtensionAbility runs in an independent process for UI layout and rendering.

It is usually used in modular development scenarios where process isolation is required.

> **NOTE**

## Constraints

The **EmbeddedComponent** is supported only on devices configured with multi-process permissions.

The **EmbeddedComponent** can be used only in the UIAbility, and the EmbeddedUIExtensionAbility to start must belong to the same application as the UIAbility.

## Child Components

Not supported

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
  loader: import('../api/@ohos.app.ability.Want').default,
  type: EmbeddedType
)
```

Creates a cross-process embedded component to display the UI of the EmbeddedUIExtensionAbility with the same bundle name.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | Yes | EmbeddedUIExtensionAbility to load. |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | Yes | Type of the provider. |

## EmbeddedComponent

```TypeScript
EmbeddedComponent(
  loader: import('../api/@ohos.app.ability.Want').default,
  type: EmbeddedType,
  options?: EmbeddedOptions
)
```

Construct the EmbeddedComponent.<br> Called when the EmbeddedComponent is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| loader | import('../api/@ohos.app.ability.Want').default | Yes | indicates initialization parameter. |
| type | [EmbeddedType](../arkts-apis/arkts-arkui-embeddedtype-e.md) | Yes | indicates type of the EmbeddedComponent. |
| options | [EmbeddedOptions](arkts-arkui-embeddedoptions-i.md) | No | construction configuration of EmbeddedComponent. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [EmbeddedOptions](arkts-arkui-embeddedoptions-i.md) | This interface is used to set the options for EmbeddedComponentAttribute during construction |
| [TerminationInfo](arkts-arkui-terminationinfo-i.md) | Provides the result returned by the started **EmbeddedUIExtensionAbility**. |

### Enums

| Name | Description |
| --- | --- |
| [EmbeddedDpiFollowStrategy](arkts-arkui-embeddeddpifollowstrategy-e.md) | Enumeration of different types of EmbeddedDpiFollowStrategy. |
| [EmbeddedWindowModeFollowStrategy](arkts-arkui-embeddedwindowmodefollowstrategy-e.md) | Enumeration of different types of EmbeddedWindowModeFollowStrategy. |
