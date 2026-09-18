# @ohos.uiExtensionHost

Intended only for the **UIExtensionComponent** that has process isolation requirements, the **uiExtensionHost** module provides APIs for obtaining the host application window information and information about the component itself.

> **NOTE:** 
> 
> No new function will be added to this module. Related functions will be provided in the
> [uiExtension](arkts-arkui-arkui-uiextension.md) interface.
> 
> The APIs provided by this module are system APIs.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiExtensionHost } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [UIExtensionHostWindowProxy](arkts-arkui-uiextensionhost-uiextensionhostwindowproxy-i-sys.md) | Transition Controller |
| [UIExtensionHostWindowProxyProperties](arkts-arkui-uiextensionhost-uiextensionhostwindowproxyproperties-i-sys.md) | Defines information about the host application window and **UIExtensionComponent**. |
<!--DelEnd-->

## Examples

```TypeScript
This example shows how to use all the available APIs in the UIExtensionAbility. The bundle name of the sample application, which requires a system signature, is com.example.uiextensiondemo, and the UIExtensionAbility to start is ExampleUIExtensionAbility.

The EntryAbility (UIAbility) of the sample application loads the pages/Index.ets file, whose content is as follows:
```

```TypeScript
The UIExtensionAbility to start by the UIExtensionComponent is implemented in the ets/extensionAbility/ExampleUIExtensionAbility file. The file content is as follows:
```

```TypeScript
The entry page file of the UIExtensionAbility is pages/extension.ets, whose content is as follows:
```

```TypeScript
Add an item to extensionAbilities in the module.json5 file of the sample application. The details are as follows:
```
