# SelectionContainer properties/events

```TypeScript
export declare class SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>
```

Defines the attributes of SelectionContainer.

**Inheritance/Implementation:** SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,
    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>)
```

Bind to the selection menu.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>The duration required for a long-press gesture is 600 ms for bindSelectionMenu and 800 ms for bindContextMenu. <br>When both bindSelectionMenu and bindContextMenu are set and both are configured to be triggered by a long-press gesture, bindSelectionMenu is triggered first. <br>If the custom menu is too long, embed a Scroll component to prevent the keyboard from being blocked. </p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextSpanType](arkts-arkui-text-comp-textspantype-e.md)&gt; | Yes | Indicates the type of selection menu. Default value is TextSpanType.TEXT. |
| content | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)&gt; | Yes | Indicates the content of selection menu. |
| responseType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextResponseType](arkts-arkui-text-comp-textresponsetype-e.md)&gt; | Yes | Indicates response type of selection menu. Default value is TextResponseType.LONG_PRESS. |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainermenuoptions-i.md)&gt; | No | Indicates the options of selection menu. |

## caretColor

```TypeScript
caretColor(color: Optional<ResourceColor>)
```

Set the caret color for selected text.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | caret color. |

## copyOption

```TypeScript
copyOption(value: Optional<CopyOptions>)
```

Set whether to allow copy and where data can be copied.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md)&gt; | Yes | copy option for selected text. Default value is CopyOptions.InApp. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>)
```

Set the custom text menu. Sets the extended options of the custom context menu on selection, including the text content, icon, and callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerEditMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainereditmenuoptions-i.md)&gt; | Yes | Customize text menu options. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: Optional<boolean>)
```

Enable or disable haptic feedback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | whether to enable haptic feedback. Default value is true. |

## onCopy

```TypeScript
onCopy(callback: Optional<Callback<string>>)
```

Called when selected text is copied. Currently, only text can be copied.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;string&gt;&gt; | Yes | callback of copy event. The callback parameter (string) is the selected text concatenated in the visual order of Text components. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: Optional<Callback<Array<string>>>)
```

Called when text selection changes in SelectionContainer.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;Array&lt;string&gt;&gt;&gt; | Yes | callback of selection change event. The order of items in the first callback parameter array is consistent with the visual order of Text components. |

## onWillCopy

```TypeScript
onWillCopy(callback: Optional<Callback<string, boolean>>)
```

Called before using the Clipboard copy menu. Currently, only text can be copied.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;string, boolean&gt;&gt; | Yes | callback used to check whether copy is allowed. The first callback parameter (string) is the selected text concatenated in the visual order of Text components. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ResourceColor>)
```

Set selected text background color.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | selected text background color. |

## textJoinStyle

```TypeScript
textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>)
```

Set text join style for aggregated text in SelectionContainer.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>This setting affects the string value used in callbacks such as onWillCopy and onCopy. <br>It also affects built-in text menu item logic that depends on string concatenation, such as copy. <br>The default style is SelectionContainerTextJoinStyle.NEWLINE. </p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerTextJoinStyle](arkts-arkui-selectioncontainer-comp-selectioncontainertextjoinstyle-e.md)&gt; | Yes | text join style for aggregated text. |
