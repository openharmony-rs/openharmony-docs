# SelectionMenuOptions

```TypeScript
export interface SelectionMenuOptions
```

Describes the optional menu type items and their configuration parameters for **SelectionMenu**.

**Since:** 11

<!--Device-unnamed-export interface SelectionMenuOptions--><!--Device-unnamed-export interface SelectionMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## onCopy

```TypeScript
onCopy?: (event?: EditorEventInfo) => void
```

Event callback that replaces the copy option of the built-in system menu.

Prerequisite: The controller parameter must be provided. The built-in copy function can be replaced only when the system default menu exists.

**NOTE:** 

event is the return information.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-onCopy?: (event?: EditorEventInfo) => void--><!--Device-SelectionMenuOptions-onCopy?: (event?: EditorEventInfo) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | No |  |

## onCut

```TypeScript
onCut?: (event?: EditorEventInfo) => void
```

Event callback that replaces the cut option of the built-in system menu.

Prerequisite: The controller parameter must be provided. The built-in cut function can be replaced only when the system default menu exists.

**NOTE:** 

event is the return information.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-onCut?: (event?: EditorEventInfo) => void--><!--Device-SelectionMenuOptions-onCut?: (event?: EditorEventInfo) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | No |  |

## onPaste

```TypeScript
onPaste?: (event?: EditorEventInfo) => void
```

Event callback that replaces the paste option of the built-in system menu.

Prerequisite: The controller parameter must be provided. The built-in paste function can be replaced only when the system default menu exists.

**NOTE:** 

event is the return information.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-onPaste?: (event?: EditorEventInfo) => void--><!--Device-SelectionMenuOptions-onPaste?: (event?: EditorEventInfo) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | No |  |

## onSelectAll

```TypeScript
onSelectAll?: (event?: EditorEventInfo) => void
```

Event callback that replaces the select all option of the built-in system menu.

Prerequisite: The controller parameter must be provided. The built-in select all function can be replaced only when the system default menu exists.

**NOTE:** 

event is the return information.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-onSelectAll?: (event?: EditorEventInfo) => void--><!--Device-SelectionMenuOptions-onSelectAll?: (event?: EditorEventInfo) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | No |  |

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

System material used for the menu background panel, which implements visual effects (such as blur and transparency) for the menu background. Different system materials contain different attributes, affecting the final display effect. For specific material types and attributes, see [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md). Default value: undefined, no material effect.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionMenuOptions-backgroundSystemMaterial?: uiMaterial.Material--><!--Device-SelectionMenuOptions-backgroundSystemMaterial?: uiMaterial.Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: RichEditorController
```

When the rich text controller is not empty, the default system menu (including cut, copy, paste, and other options) is displayed and the default menu functions are built-in.

When controller is empty, the More button is not displayed. If expandedMenuOptions is not empty, the items are displayed in the dropdown menu.

By default, the system only supports copying and pasting rich text content. For mixed text and images, the app needs to customize the onCopy and onPaste APIs. When the app configures the onCopy | onPaste APIs, the system menu's default copy and paste become invalid, and the app's custom functions are called instead.

**NOTE:** 

After tapping the built-in copy option in the custom text selection menu, the custom menu disappears and the selected text highlight is retained.

After tapping the built-in select all option in the custom text selection menu, the custom menu disappears and all text is selected and highlighted.

After tapping the built-in paste option in the custom text selection menu, pasting in a blank area or replacing selected text with paste both retain the style of the copied text.

When the copyOptions attribute of the rich text component [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md) is set to `CopyOptions.None`, the built-in copy and cut functions are not restricted.

**Type:** [RichEditorController](../arkts-components/arkts-arkui-richeditor-comp-richeditorcontroller-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-controller?: RichEditorController--><!--Device-SelectionMenuOptions-controller?: RichEditorController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## editorMenuOptions

```TypeScript
editorMenuOptions?: Array<EditorMenuOptions>
```

Edit menu.

When **editorMenuOptions** is not configured, the edit menu is not displayed.

When both **action** and **builder** in **EditorMenuOptions** are configured, tapping the icon triggers both responses.

Tapping an edit menu icon does not close the entire menu by default. The app can configure **RichEditorController**'s **closeSelectionMenu** through the **action** API to actively close the menu.

**Type:** Array&lt;[EditorMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-editormenuoptions-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-editorMenuOptions?: Array<EditorMenuOptions>--><!--Device-SelectionMenuOptions-editorMenuOptions?: Array<EditorMenuOptions>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expandedMenuOptions

```TypeScript
expandedMenuOptions?: Array<ExpandedMenuOptions>
```

Extended dropdown menu.

When expandedMenuOptions is empty, there is no More button and the extended dropdown menu is not displayed.

When expandedMenuOptions is not empty, the More button is displayed, and the configured menu items are collapsed in the More button. Tap the More button to display them.

When controller is empty, the More button is not displayed. If expandedMenuOptions is not empty, the items are displayed in the dropdown menu.

**Type:** Array&lt;[ExpandedMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-expandedmenuoptions-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SelectionMenuOptions-expandedMenuOptions?: Array<ExpandedMenuOptions>--><!--Device-SelectionMenuOptions-expandedMenuOptions?: Array<ExpandedMenuOptions>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
