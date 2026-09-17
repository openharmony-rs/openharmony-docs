# UIExtensionComponent(System API) (System API)

**UIExtensionComponent** is used to embed UIs provided by other applications in the local application UI. The embedded content runs in another process, and the local application does not participate in its layout and rendering.

It is usually used in modular development scenarios where process isolation is required.

## Constraints

This component does not support preview.

The ability to be started must be a UIExtensionAbility, an extension ability with UI. For details about how to implement a UIExtensionAbility, see [@ohos.app.ability.UIExtensionAbility (Base Class for ExtensionAbilities with UI)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md).

The width and height of the component must be explicitly set to non-zero valid values.

The scenario where scrolling continues after the edge is reached is not supported. When both the **UIExtensionComponent** host and the UIExtensionAbility support content scrolling, gesture-based scrolling will cause simultaneous responses from both inside and outside the **UIExtensionComponent**. This includes, but is not limited to, scrollable containers such as Scroll, Swiper, List, and Grid. For details about how to avoid the simultaneous scrolling inside and outside the **UIExtensionComponent**, see [Example 2](../../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent).

## Child Components

Not supported

## UIExtensionComponent

```TypeScript
UIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: UIExtensionOptions
  )
```

Construct the UIExtensionComponent.<br> Called when the UIExtensionComponent is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | import('../api/@ohos.app.ability.Want').default | Yes | Ability to start. |
| options | [UIExtensionOptions](arkts-arkui-uiextensionoptions-i-sys.md) | No | Construction parameters. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TerminationInfo](arkts-arkui-terminationinfo-i-sys.md) | Indicates the information when the provider of the embedded UI is terminated. |
| [UIExtensionOptions](arkts-arkui-uiextensionoptions-i-sys.md) | Describes the optional construction parameters during **UIExtensionComponent** construction. |
| [UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md) | Implements a **UIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started UIExtensionAbility through the connection established between the two parties. |

### Types

| Name | Description |
| --- | --- |
| [ReceiveCallback](arkts-arkui-receivecallback-t-sys.md) | Triggered to encapsulate the data sent by the started ability. |

### Enums

| Name | Description |
| --- | --- |
| [DpiFollowStrategy](arkts-arkui-dpifollowstrategy-e-sys.md) | Enumeration of different types of DpiFollowStrategy. |
| [WindowModeFollowStrategy](arkts-arkui-windowmodefollowstrategy-e-sys.md) | Enumerates the following strategies of the window mode. |

## Examples

```TypeScript
### Example 1: Loading a UIExtension

The UIExtensionComponent component can be used by both the host and provider. This example shows only the method used by the component and the UIExtensionAbility. For the code to run properly, you need to install the ability whose bundleName is com.example.newdemo and abilityName is UIExtensionProvider on the device.

Component host

The content of the user's entry page Index.ets is as follows:
```

```TypeScript
Component provider

The provider has three files that need to be modified:

/src/main/ets/uiextensionability/UIExtensionProvider.ets
```

```TypeScript
Entry page file of the provider's extension Ability: /src/main/ets/pages/extension.ets
```

```TypeScript
The provider's extension Ability. Add the corresponding configuration to the module configuration file /src/main/module.json5.
```

```TypeScript
### Example 2: Isolating Scrolling Inside and Outside of UIExtensionComponent

This example demonstrates a scenario where both the UIExtensionComponent host and the UIExtensionAbility use [Scroll](ts-container-scroll.md) containers. By setting gesture interception on UIExtensionComponent, it achieves that external components do not respond to scrolling when the internal layer of the UIExtensionComponent is being scrolled.

Gesture usage:

Scrolling inside the component: scrolling within the component using touch gestures

Scrolling outside the component: scrolling of the outer container using the scrollbar

Before running, ensure that an ability whose bundleName is com.example.newdemo and abilityName as UIExtensionProvider is installed on the device.

The entry point file UIExtensionProvider.ets and the module configuration file UIExtensionProvider.ets are identical to those in [Example 1](#example-1-loading-a-uiextension).

The provider's extension Ability and module configuration file are the same as the module.json5 code of the extension module in [Example 1](#example-1-loading-a-uiextension).

Example of the user's component usage:
```

```TypeScript
extension.ets (entry page file of the provider's UIExtensionAbility)
```
