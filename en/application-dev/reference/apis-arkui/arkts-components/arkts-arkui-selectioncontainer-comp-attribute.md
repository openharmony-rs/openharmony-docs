# SelectionContainer properties/events

```TypeScript
export declare class SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>
```

[Universal attributes](arkts-arkui-common-comp.md) are supported.

> **NOTE:** 
> 
> - The [obscuring](arkts-arkui-common-comp.md) attribute is not supported.
> 
> - The [transformation](arkts-arkui-common-comp.md) attribute is not supported. In the
> **SelectionContainer** container, the **Text** child component does not support transformation.

**Inheritance/Implementation:** SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>

**Since:** 26.0.0

<!--Device-unnamed-export declare class SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>--><!--Device-unnamed-export declare class SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>-End-->

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

Sets a custom selection menu. If this attribute is not used, the default value of **spanType** is **TextSpanType.TEXT** and the default value of **responseType** is **TextResponseType.LONG_PRESS**.

> **NOTE:** 
> 
> - The long-press response duration of **bindSelectionMenu** is 600 ms, while that of [bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu)is 800 ms. When both are bound and both are triggered by a long press, **bindSelectionMenu** is responded to first.
> 
> - When the custom menu is too long, you are advised to nest a [Scroll](arkts-arkui-scroll-comp.md)component inside it to prevent the keyboard from being obscured.
> 
> - When the selection spans non-copyable text, the menu is displayed and processed based only on the copyable text actually selected.
> 
> - In the **SelectionContainer** container, the [bindSelectionMenu](arkts-arkui-text-comp-attribute.md#bindselectionmenu) setting of the **Text** child component does not take effect, and the configuration of **SelectionContainer** is always used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| spanType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextSpanType](arkts-arkui-text-comp-textspantype-e.md)&gt; | Yes | Type of the selection menu. It specifies the range of text types to which the selection menu applies. Different types correspond to different menu behaviors. For details about the meaning and applicable scenarios of each enum value, see [TextSpanType](arkts-arkui-text-comp-textspantype-e.md). |
| content | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)&gt; | Yes | Content of the selection menu. |
| responseType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextResponseType](arkts-arkui-text-comp-textresponsetype-e.md)&gt; | Yes | Response type of the selection menu. |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainermenuoptions-i.md)&gt; | No | Options of the selection menu, used to configure callbacks for events such as menu appearance, disappearance, display, and hiding. Pass this parameter when you need to listen for these menu events. If it is not passed, menu events are not listened for by default. |

## caretColor

```TypeScript
caretColor(color: Optional<ResourceColor>)
```

Sets the caret color of the selected text. If this attribute is not used, the default caret color is **'#007DFF'** (blue).

> **NOTE:** 
> 
> - In the **SelectionContainer** container, this attribute is used to set the caret color of the selected text in each **Text** child component.
> 
> - In the **SelectionContainer** container, the [caretColor](arkts-arkui-text-comp-attribute.md#caretcolor) setting of the
> **Text** child component does not take effect, and the configuration of **SelectionContainer** is always used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-caretColor(color: Optional<ResourceColor>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-caretColor(color: Optional<ResourceColor>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Caret color. |

## copyOption

```TypeScript
copyOption(value: Optional<CopyOptions>)
```

Sets the copy option for the component. If this attribute is not used, the default value is **CopyOptions.InApp**.

> **NOTE:** 
> 
> If the **Text** child component has explicitly set [copyOption](arkts-arkui-text-comp-attribute.md#copyoption), the
> configuration of the **Text** child component takes precedence. If this attribute is not set, the configuration
> of **SelectionContainer** is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-copyOption(value: Optional<CopyOptions>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-copyOption(value: Optional<CopyOptions>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md)&gt; | Yes | Copy and paste configuration item, used to set the copyable range of text. For details, see the CopyOptions enum. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>)
```

Sets the edit menu options for the selected text, including the menu text, icon, and callback.

> **NOTE:** 
> 
> - When both [bindSelectionMenu](#bindselectionmenu) and **editMenuOptions** are set for the current scenario, **bindSelectionMenu** takes precedence and **editMenuOptions** does not take effect. **bindSelectionMenu** is used to fully customize the menu style and trigger conditions, with all menu items defined by you. **editMenuOptions** is used to add extension items on top of the system default menu, with the trigger conditions unchanged. It is recommended that you choose based on the required degree of customization.
> 
> - In the **SelectionContainer** container, the [editMenuOptions](arkts-arkui-text-comp-attribute.md#editmenuoptions) setting of the **Text** child component does not take effect, and the configuration of **SelectionContainer** is always used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editMenu | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerEditMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainereditmenuoptions-i.md)&gt; | Yes | Custom edit menu configuration. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: Optional<boolean>)
```

Sets whether to enable haptic feedback. If this attribute is not used, haptic feedback is enabled by default.

When haptic feedback is enabled, you need to set the **requestPermissions** field in the [module.json5 configuration file](../../../quick-start/module-configuration-file.md) of the project to enable the vibration permission. The configuration is as follows:

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-enableHapticFeedback(isEnabled: Optional<boolean>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-enableHapticFeedback(isEnabled: Optional<boolean>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable haptic feedback.<br>true indicates that haptic feedback is enabled, and false indicates that haptic feedback is disabled. |

## onCopy

```TypeScript
onCopy(callback: Optional<Callback<string>>)
```

Triggered when the copy button on the selection menu is tapped after the selection menu is displayed by long- pressing the inner area of the text. Only text copying is supported. This API returns the result asynchronously through a callback.

> **NOTE:** 
> 
> - The callback parameter is the selected text concatenated in the visual order of the **Text** components. The concatenation method is determined by [textJoinStyle](#textjoinstyle).
> 
> - This callback is triggered only when the container-level [onWillCopy](#onwillcopy) returns **true**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-onCopy(callback: Optional<Callback<string>>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-onCopy(callback: Optional<Callback<string>>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;string&gt;&gt; | Yes | Callback for the copy event. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: Optional<Callback<Array<string>>>)
```

Triggered when the selected text in **SelectionContainer** changes. This API returns the result asynchronously through a callback.

> **NOTE:** 
> 
> - The order of items in the callback parameter array is consistent with the visual order of the **Text**components.
> 
> - Each item in the array corresponds to the selected text of a **Text** child component.
> 
> - The array contains only **Text** child components that have selected text. It does not include **Text** child components without selected text, nor does it include empty string placeholders for non-copyable text.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-onTextSelectionChange(callback: Optional<Callback<Array<string>>>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-onTextSelectionChange(callback: Optional<Callback<Array<string>>>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;Array&lt;string&gt;&gt;&gt; | Yes | Callback invoked when the selected text changes. |

## onWillCopy

```TypeScript
onWillCopy(callback: Optional<Callback<string, boolean>>)
```

Triggered before a copy operation is performed. This API returns the result asynchronously through a callback.

> **NOTE:** 
> 
> - The callback parameter is the selected text concatenated in the visual order of the **Text** components, and the concatenation method is determined by [textJoinStyle](#textjoinstyle).
> 
> - Returning **false** blocks this cross-node copy operation and the container-level [onCopy](#oncopy) callback triggering, but does not affect the copy event logic that each **Text** child component has already processed independently.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-onWillCopy(callback: Optional<Callback<string, boolean>>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-onWillCopy(callback: Optional<Callback<string, boolean>>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;string, boolean&gt;&gt; | Yes | Callback invoked before copying. Returning **true** indicates that copying is allowed, and returning **false** indicates that copying is not allowed. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ResourceColor>)
```

Sets the highlight color of the selected text. If this attribute is not used, the default highlight color of the selected text is **'#007DFF'** (blue). If the opacity is not set or is set to fully opaque, the default opacity is 20%.

> **NOTE:** 
> 
> - In the **SelectionContainer** container, this attribute is used to control the highlight color of the selected area of each **Text** child component.
> 
> - If the **Text** child component has explicitly set [selectedBackgroundColor](arkts-arkui-text-comp-attribute.md#selectedbackgroundcolor), the configuration of the **Text** child component takes preference. Otherwise, use the configuration of **SelectionContainer**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-selectedBackgroundColor(color: Optional<ResourceColor>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-selectedBackgroundColor(color: Optional<ResourceColor>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Highlight color of the selected text. |

## textJoinStyle

```TypeScript
textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>)
```

Sets the concatenation method for the aggregated text in **SelectionContainer**. If this attribute is not used, the default value is **SelectionContainerTextJoinStyle.NEWLINE**, which means that different text nodes are concatenated with newline characters (\n).

> **NOTE:** 
> 
> - This configuration affects the text content returned in the callbacks of [onWillCopy](#onwillcopy), [onCopy](#oncopy),and [bindSelectionMenu](#bindselectionmenu).
> 
> - This configuration also affects the logic that depends on the text concatenation result in the built-in system menu items. For example, when text in two **Text** nodes is selected, if the configuration is
> **SelectionContainerTextJoinStyle.NEWLINE**, a newline character is inserted between the two text segments after
> copying; if the configuration is **SelectionContainerTextJoinStyle.DIRECT**, the two text segments are directly
> concatenated after copying.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SelectionContainerAttribute-textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>): SelectionContainerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerTextJoinStyle](arkts-arkui-selectioncontainer-comp-selectioncontainertextjoinstyle-e.md)&gt; | Yes | Text concatenation mode of the aggregated text. |
