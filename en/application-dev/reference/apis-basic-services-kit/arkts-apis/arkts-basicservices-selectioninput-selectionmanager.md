# @ohos.selectionInput.selectionManager(Word Selection Management)

This module provides word selection management capabilities, including creating, displaying, moving, hiding, and destroying panels, listening for word selection events using a mouse or touchpad, and retrieving the selected text. The typical usage process is as follows:
1. Call [on('selectionCompleted')](arkts-basicservices-selectionmanager-on-f.md) to subscribe to the selection completion event.
2. In the callback, call [getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f.md) to obtain the selected text.
3. Call [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md) to create a word selection panel.
4. Call [setUiContent](arkts-basicservices-selectionmanager-panel-i.md#setuicontent) to load the page content.
5. Call [moveToGlobalDisplay](arkts-basicservices-selectionmanager-panel-i.md#movetoglobaldisplay) to move the panel to the specified position.
6. Call [show](arkts-basicservices-selectionmanager-panel-i.md#show) to display the panel.
7. Call [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md) to destroy the panel.
8. Call [off('selectionCompleted')](arkts-basicservices-selectionmanager-off-f.md) to unsubscribe from the selection completion event.

> **NOTE:** 
> 
> - This module is supported only on PCs/2-in-1 devices. You can use
> **canIUse('SystemCapability.SelectionInput.Selection')** to check whether the current device supports this
> function.
> - APIs of this module can be called only by apps that integrate the extension ability for word selection. For details about how to implement the extension ability for word selection, see [SelectionExtensionAbility](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c.md).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.SelectionInput.Selection

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md) | Creates a word selection panel, which is used to display the service-related operation UI or text processing result. After the panel is used, call [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md) to destroy the panel and release resources. This API uses a promise to return the result. |
| [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md) | Destroys the word selection panel. This API is used together with [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md) to destroy the panel object created by **createPanel()**. This API uses a promise to return the result. |
| [getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f.md) | Obtains the content of the selected text. This API uses a promise to return the result. This API must be called in the [on('selectionCompleted')](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted) callback and is valid only after the word selection completion event is triggered. |
| [off](arkts-basicservices-selectionmanager-off-f.md#offselectioncompleted) | Unsubscribes from the word selection completion event. This API is used together with [on('selectionCompleted')](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted). |
| [on](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted) | Subscribes to the word selection completion event. This API is used together with [off('selectionCompleted')](arkts-basicservices-selectionmanager-off-f.md#offselectioncompleted). |

### Interfaces

| Name | Description |
| --- | --- |
| [Panel](arkts-basicservices-selectionmanager-panel-i.md) | Describes a **Panel** object, which is created using [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This method can be used to set, display, hide, and move the panel, as well as subscribe to events. It is applicable to scenarios where a custom operation UI needs to be displayed to users after word selection is complete. |
| [SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i.md) | Defines the information of a word selection event. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Panel](arkts-basicservices-selectionmanager-panel-i-sys.md) | Describes a **Panel** object, which is created using [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md). This method can be used to set, display, hide, and move the panel, as well as subscribe to events. It is applicable to scenarios where a custom operation UI needs to be displayed to users after word selection is complete. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SelectionType](arkts-basicservices-selectionmanager-selectiontype-e.md) | Enumerates the word selection types. |
