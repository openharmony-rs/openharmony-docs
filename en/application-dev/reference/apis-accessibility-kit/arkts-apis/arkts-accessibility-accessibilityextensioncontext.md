# AccessibilityExtensionContext(Provides accessibility extension context)

The Accessibility Extension Context module provides a context environment, supporting accessibility apps in
 configuring information types of interest, querying node information, gesture injection, and more.



## Summary

### Classes

| Name | Description |
| --- | --- |
| [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md) | The **AccessibilityExtensionContext** module, inherited from **ExtensionContext**, provides context for **AccessibilityExtensionAbility**. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c-sys.md) | The **AccessibilityExtensionContext** module, inherited from **ExtensionContext**, provides context for **AccessibilityExtensionAbility**. |
| [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md) | Provides parameter values for specific settings when an accessibility node element performs a specific action. Different action types require different parameter fields. For details about the mapping between action types and parameter fields, see [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md) (actions that can be performed by an accessibility node element). |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md) | An accessibility node element that provides capabilities such as querying parent/child elements, finding elements by content or focus direction, and performing accessibility actions. It is applicable to scenarios where an accessibility app needs to interact with and operate on UI nodes. |
| [ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i.md) | Provides attribute names and value types of a node element. |
| [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md) | Defines a rectangle. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i-sys.md) | An accessibility node element that provides capabilities such as querying parent/child elements, finding elements by content or focus direction, and performing accessibility actions. It is applicable to scenarios where an accessibility app needs to interact with and operate on UI nodes. |
| [AccessibilityGrid](arkts-accessibility-accessibilityextensioncontext-accessibilitygrid-i-sys.md) | Accessibility grid information. For details, see the property currentItem in [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md). |
| [AccessibilitySpan](arkts-accessibility-accessibilityextensioncontext-accessibilityspan-i-sys.md) | Hyperlink text information for accessibility. For details, see the attribute spans in [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md). |
| [AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md) | Defines an accessibility virtual node. |
| [ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i-sys.md) | Provides attribute names and value types of a node element. |
| [FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md) | Return value type of the accessibility node query. |
| [TouchPosition](arkts-accessibility-accessibilityextensioncontext-touchposition-i-sys.md) | Touch tap position. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [FocusDirection](arkts-accessibility-focusdirection-t.md) | Enumerates the focus directions. |
| [FocusType](arkts-accessibility-focustype-t.md) | Enumerates the focus types. |
| [WindowType](arkts-accessibility-windowtype-t.md) | Enumerates the window types. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | Describes the method for querying focusable nodes. |
| [FocusRule](arkts-accessibility-focusrule-t-sys.md) | Describes how to determine the focus capability of the starting node and its child nodes when searching for focusable nodes. |
<!--DelEnd-->
