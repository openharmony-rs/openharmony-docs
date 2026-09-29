# EditorEventInfo

```TypeScript
export interface EditorEventInfo
```

Provides the information about the selected content.

**Since:** 11

<!--Device-unnamed-export interface EditorEventInfo--><!--Device-unnamed-export interface EditorEventInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## content

```TypeScript
content?: RichEditorSelection
```

Information about the selected content, including the selected text or image spans and the selection range.

**Type:** [RichEditorSelection](../arkts-components/arkts-arkui-richeditor-comp-richeditorselection-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditorEventInfo-content?: RichEditorSelection--><!--Device-EditorEventInfo-content?: RichEditorSelection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
