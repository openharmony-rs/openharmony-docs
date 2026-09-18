# @ohos.arkui.uiExtension

The **uiExtension** module provides APIs for the [EmbeddedUIExtensionAbility](../../../application-models/embeddeduiextensionability.md) (or [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)) to obtain the host application window information or the information about the corresponding EmbeddedComponent<!--Del--> (or UIExtensionComponent)<!--DelEnd--> component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md) | Represents the information about the avoidance area of the window. |
| [RectChangeOptions](arkts-arkui-uiextension-rectchangeoptions-i.md) | Provides the values and reasons returned when the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**) changes. |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i.md) | The proxy of the UIExtension window. |
| [WindowProxyProperties](arkts-arkui-uiextension-windowproxyproperties-i.md) | Provides information about a component. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i-sys.md) | The proxy of the UIExtension window. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [EventFlag](arkts-arkui-uiextension-eventflag-e.md) | Enumerates event types. |
| [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md) | Enumerates the reasons for changes in the rectangle (position and size) of the component (**EmbeddedComponent** or **UIExtensionComponent**). |

## Examples

```TypeScript
This example shows how to use all the available APIs in the [EmbeddedUIExtensionAbility](../../../application-models/embeddeduiextensionability.md). The bundle name of the sample application is com.example.embeddeddemo, and the EmbeddedUIExtensionAbility to start is ExampleEmbeddedAbility.

The EntryAbility (UIAbility) of the sample application loads the pages/Index.ets file, whose content is as follows:
```

```TypeScript
The EmbeddedUIExtensionAbility to start by the EmbeddedComponent is implemented in the ets/extensionAbility/ExampleEmbeddedAbility file. The file content is as follows:
```

```TypeScript
The entry page file of the EmbeddedUIExtensionAbility is pages/extension.ets, whose content is as follows:
```

```TypeScript
Add an item to extensionAbilities in the module.json5 file of the sample application. The details are as follows:
```
