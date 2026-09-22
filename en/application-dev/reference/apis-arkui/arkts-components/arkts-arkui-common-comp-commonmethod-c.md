# CommonMethod

```TypeScript
declare class CommonMethod<T>
```

CommonMethod.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityActionOptions

```TypeScript
accessibilityActionOptions(option: AccessibilityActionOptions | undefined): T
```

Provides optional parameters for setting accessibility operations of a component, which is used to restrict or <br>modify the operations initiated by accessibility applications such as the screen reader.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [AccessibilityActionOptions](../arkts-apis/arkts-arkui-accessibilityactionoptions-i.md) &#124; undefined | Yes | Parameter of the accessibility operation, which is used<br>to restrict or modify the sliding behavior in the accessibility operation. <br>The **scrollStep** parameter in **AccessibilityActionOptions** is used to set the number of sliding steps in <br>the accessibility operation. When the value is **undefined**, **scrollStep** is processed as **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return component instance who call the method. |

## accessibilityChecked

```TypeScript
accessibilityChecked(isCheck: boolean): T
```

Sets the checked state for the accessibility node. This API is used in multi-select scenarios and only affects <br>component state announcements in screen reading scenarios.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**Widget capability:** This API can be used in ArkTS widgets since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isCheck | boolean | Yes | Whether the current component is selected.<br>**true**: The component is selected. <br>**false**: The component is not selected. <br>**undefined**: The component determines its own selected state. <br>Default value: **undefined** |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityCustomActions

```TypeScript
accessibilityCustomActions(actions: Array<AccessibilityCustomAction> | undefined): T
```

Sets the custom accessibility operations of the component, allowing developers to set an array of custom actions <br>for binding custom operation callbacks to components by operation name.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actions | Array&lt;[AccessibilityCustomAction](../arkts-apis/arkts-arkui-accessibilitycustomaction-i.md)&gt; &#124; undefined | Yes | Array of custom accessibility operations, where<br>each operation contains an operation name and a callback, used for binding custom operation callbacks to <br>components by operation name. <br>**NOTE:**  The array supports a maximum of 16 entries; any excess will not take effect. <br>When the value is **undefined**, no custom operations are set. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return component instance who call method. |

## accessibilityDefaultFocus

```TypeScript
accessibilityDefaultFocus(focus: boolean): T
```

Sets the initial screen reader focus on the page.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| focus | boolean | Yes | Initial screen reader focus on the page. The value **true** means the component is the<br>default initial focus for screen readers on the current page. Other values are ignored. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityDescription

```TypeScript
accessibilityDescription(value: string): T
```

Sets the accessibility description. <br>This attribute provides additional context and explanation for the component, helping users understand its <br>functionality and purpose.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Accessibility description. You can specify further explanation of the current component,<br>such as potential operation consequences that cannot be inferred from component attributes or accessibility text. <br>If a component contains both text content and the accessibility description, the screen reader announces the <br>text first, followed by the accessibility description, when the component is selected. <br>Default value: **""** |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="accessibilitydescription-1"></a>

## accessibilityDescription

```TypeScript
accessibilityDescription(description: Resource): T
```

Sets the accessibility description, with support for resource references using Resource. <br>This attribute provides additional context and explanation for the component, helping users understand its <br>functionality and purpose. <p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>Reference resource of the accessibility description. You can specify further explanation <br>of the current component, for example, possible operation consequences, especially those that <br>cannot be learned from component attributes and accessibility text. If a component contains <br>both text information and the accessibility description, the text is read first and then the <br>accessibility description, when the component is selected.</p>

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | set description of accessibility |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityFocusDrawLevel

```TypeScript
accessibilityFocusDrawLevel(drawLevel: FocusDrawLevel): T
```

Sets the drawing level for the accessibility focus highlight (green frame).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawLevel | [FocusDrawLevel](../arkts-apis/arkts-arkui-focusdrawlevel-e.md) | Yes | Drawing level for the accessibility focus highlight frame. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityGroup

```TypeScript
accessibilityGroup(value: boolean): T
```

Sets whether to enable accessibility grouping.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>Whether to enable accessibility grouping. When accessibility grouping is enabled, <br>the component and all its children are treated as a single selectable unit, and the accessibility <br>service will no longer focus on the individual child components.</p>

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | set group with accessibility, default value is false. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="accessibilitygroup-1"></a>

## accessibilityGroup

```TypeScript
accessibilityGroup(isGroup: boolean, accessibilityOptions: AccessibilityOptions): T
```

Sets whether to enable accessibility grouping.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>If accessibility grouping is enabled and the component does not contain a universal text attribute <br>or an accessibility text attribute, the system will concatenate the universal text attributes of <br>its child components to form a merged text for the component. If a child component lacks a universal <br>text attribute, it will be ignored in the concatenation process.

<br>When accessibilityPreferred is set to true, the system will prioritize concatenating the accessibility <br>text attributes of the child components to form the merged text. If a child component lacks an <br>accessibility text attribute, the system will continue to concatenate its universal text attribute. <br>If a child component lacks both, it will be ignored.</p>

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**Widget capability:** This API can be used in ArkTS widgets since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isGroup | boolean | Yes | set group with accessibility, default value is false. |
| accessibilityOptions | AccessibilityOptions | Yes | accessibilityOptions for accessibility, default value is false. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityLevel

```TypeScript
accessibilityLevel(value: string): T
```

Sets the accessibility level. This property determines whether the component can be recognized by accessibility services. <p> Accessibility level, which is used to decide whether a component can be identified by the accessibility service. <br>The options are as follows: <br>"auto": The component's recognizability is determined by the accessibility grouping service and ArkUI. <br>"yes": The component can be recognized by accessibility services. <br>"no": The component cannot be recognized by accessibility services. <br>"no-hide-descendants": Neither the component nor its child components can be recognized by accessibility services. &lt;strong&gt;NOTE&lt;/strong&gt; <br>When accessibilityLevel is set to "auto", the component's recognizability depends on the following factors: <br>1. The accessibility service internally determines whether the component can be recognized. <br>2. If the parent component's accessibilityGroup property has isGroup set to true, the accessibility service will <br>not focus on its child components, making them unrecognizable. <br>3. If the parent component's accessibilityLevel is set to "no-hide-descendants", the component will not be <br>recognized by accessibility services.</p>

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | set accessibility level, default value is auto. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId(nextId: string): T
```

Sets the next component to receive focus during screen reader navigation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nextId | string | Yes | [Unique ID](#id) of the next component to receive focus. <br>If the ID does not correspond to any component, the setting is ignored. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="accessibilitynextfocusid-1"></a>

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId(nextId: string, nextFocusParams : AccessibilityNextFocusParams | undefined): T
```

Sets the next component to receive focus during screen reader navigation, with optional detailed parameters. The detailed parameters can provide additional behavior for the accessibility focus transition.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nextId | string | Yes | [Unique ID](#id) of the next component to receive focus. <br>If the ID does not correspond to any component, the setting is ignored. |
| nextFocusParams | [AccessibilityNextFocusParams](../arkts-apis/arkts-arkui-accessibilitynextfocusparams-i.md) &#124; undefined | Yes | Detailed parameters for accessibility next<br>focus processing, used to configure whether to search for focusable nodes among descendant nodes. <br>When the value is **undefined**, no detailed parameters are configured and no focus search is performed <br>among descendant nodes. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityRole

```TypeScript
accessibilityRole(role: AccessibilityRoleType): T
```

Sets the role type of the accessibility component, which affects how the component is announced by screen readers.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| role | [AccessibilityRoleType](arkts-arkui-common-comp-accessibilityroletype-e.md) | Yes | Role of the component as announced by screen readers (for example, button or<br>chart). You can define custom roles. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityScrollTriggerable

```TypeScript
accessibilityScrollTriggerable(isTriggerable: boolean): T
```

Sets whether the accessibility node triggers automatic screen scrolling. When no focusable components are visible <br>on the current page within a container, this setting determines whether automatic scrolling is initiated.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTriggerable | boolean | Yes | Whether the component triggers automatic scrolling for screen readers when the<br>current page has no focusable components. <br>**true**: The component triggers automatic scrolling. <br>**false**: The component does not trigger automatic scrolling. <br>**undefined**: The default settings are restored. <br>Default value: **true** |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilitySelected

```TypeScript
accessibilitySelected(isSelect: boolean): T
```

Sets the checked state for the accessibility node. This API is used in single-select scenarios and only affects <br>component state announcements in screen reading scenarios.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**Widget capability:** This API can be used in ArkTS widgets since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isSelect | boolean | Yes | Whether the current component is selected.<br>**true**: The component is selected. <br>**false**: The component is not selected. <br>**undefined**: The component determines its own selected state. <br>Default value: **undefined** |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityStateDescription

```TypeScript
accessibilityStateDescription(description: string | Resource | undefined): T
```

Sets the state description of a component for broadcasting, which clearly describes the real-time state of the <br>component in screen reading scenarios. Screen reader will broadcast the state description first.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; undefined | Yes | Text to be broadcasted for the current state of the component.<br>If the text contains more than 1000 characters, the first 1000 characters will be broadcasted. <br>**undefined**: The text is empty by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return component instance who call the method. |

## accessibilityText

```TypeScript
accessibilityText(value: string): T
```

Sets the accessibility text. When a component does not contain a text attribute, you can use this API to set an accessibility text attribute, so that accessibility services can announce the specified content for the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | set accessibility text, default value is "". |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="accessibilitytext-1"></a>

## accessibilityText

```TypeScript
accessibilityText(text: Resource): T
```

Sets the accessibility text.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; If a component has both text content and accessibility text, only the accessibility text is announced. <br>If a component is grouped for accessibility purposes but lacks both text content and accessibility <br>text, the screen reader will concatenate text from its child components (depth-first traversal). <br>To prioritize accessibility text concatenation, set accessibilityPreferred in accessibilityGroup. </p>

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | set accessibility text |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityTextHint

```TypeScript
accessibilityTextHint(value: string): T
```

Sets the text hint for the component, which can be queried by accessibility services.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text hint for the component, which can be queried by accessibility services. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityUseSamePage

```TypeScript
accessibilityUseSamePage(pageMode: AccessibilitySamePageMode): T
```

Sets the same-page mode for the current component and its host application.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pageMode | [AccessibilitySamePageMode](arkts-arkui-common-comp-accessibilitysamepagemode-e.md) | Yes | Same-page mode for the cross-process embedded component<br>and the host application. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## accessibilityVirtualNode

```TypeScript
accessibilityVirtualNode(builder: CustomBuilder): T
```

Sets an accessibility virtual child node. For custom drawing components, a **CustomBuilder** is passed, which is <br>used to provide accessibility information. The components within the **CustomBuilder** are only used for layout <br>and not for display.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Accessibility virtual node. Pass a custom builder to the custom drawing component.<br>The components within the custom builder are used for layout only and are not visually rendered. When <br>accessibility services retrieve node information, the node information from the custom builder is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## align

```TypeScript
align(value: Alignment): T
```

Sets the alignment mode for child components within the component's drawing area. This attribute can be dynamically set using [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | Yes | Sets the alignment mode of child components within the drawing region of the current component. <br>This attribute takes effect only in Stack, [FolderStack](arkts-arkui-folderstack-comp.md#folderstack), [Shape](arkts-arkui-shape-comp.md#shape), Button, Marquee, [StepperItem](arkts-arkui-stepperitem-comp.md#stepperitem), Text, TextArea, TextInput, [RichEditor](arkts-arkui-richeditor-comp.md#richeditor), Hyperlink, SymbolGlyph, ListItem, GridItem, Scroll, FlowItem, [ImageAnimator](arkts-arkui-imageanimator-comp.md#imageanimator), LoadingProgress, [PatternLock](arkts-arkui-patternlock-comp.md#patternlock), Progress, QRCode, TextClock, TextTimer, [MenuItem](arkts-arkui-menuitem-comp.md#menuitem), Toggle, Checkbox, and [NodeContainer](arkts-arkui-nodecontainer-comp-attribute.md#nodecontainer). For text-related components **Marquee**, **Text**, **TextArea**, **TextInput**, **RichEditor**, and **Hyperlink**, the align result refers to [textAlign](arkts-arkui-text-comp-attribute.md#textalign). <br>Components that do not support the **textAlign** attribute cannot set horizontal text alignment. <br>Default value: **Alignment.Center** <br>**NOTE:** <br> This attribute supports mirroring on the Stack component, but not on other components. <br>In **Stack**, this attribute has the same effect as **alignContent** and can only set the alignment mode of child components within the current component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="align-1"></a>

## align

```TypeScript
align(alignment: Alignment | LocalizedAlignment): T
```

Sets the alignment mode for child components within the component's drawing area. The mirroring capability is supported. This attribute can be dynamically set using [attributeModifier](#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignment | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) &#124; [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) | Yes | Sets the alignment mode of child components within the drawing region of the current component, and adds the mirroring capability. The [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) type is effective only in the following components: [Shape](arkts-arkui-shape-comp.md#shape), Button, GridItem, FlowItem, [ImageAnimator](arkts-arkui-imageanimator-comp.md#imageanimator), LoadingProgress, [PatternLock](arkts-arkui-patternlock-comp.md#patternlock), Progress, QRCode, TextClock, TextTimer, [StepperItem](arkts-arkui-stepperitem-comp.md#stepperitem), [MenuItem](arkts-arkui-menuitem-comp.md#menuitem), Toggle, Checkbox, and ListItem. Among them, except that ListItem behaves the same as [Alignment](../arkts-apis/arkts-arkui-alignment-e.md), mirroring switching takes effect for all other components; components for which **LocalizedAlignment** has no effect are displayed according to their default behavior. <br>Default value: **Alignment.Center**, **LocalizedAlignment.CENTER** <br>If an invalid value is set, the default value is used, and the component is displayed centered. <br>**NOTE:** <br> The [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) type does not support the mirroring capability; the [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) type supports the mirroring capability. Select an enum value in [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) to implement mirroring switching based on the change of direction or the system language direction. The priority of **direction** is higher than that of the system language direction. When **direction** is set and is not **auto**, the mirroring of [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) performs layout according to **direction**; when **direction** is set to **auto** or is not set, the mirroring of [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) performs layout according to the system language direction. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## alignRules

```TypeScript
alignRules(value: AlignRuleOption): T
```

Sets the alignment rule for child components within the relative container. This attribute only takes effect when the parent container is RelativeContainer, and supports dynamic configuration via [attributeModifier](#attributemodifier).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AlignRuleOption](arkts-arkui-common-comp-alignruleoption-i.md) | Yes | Alignment rules in the relative container. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="alignrules-1"></a>

## alignRules

```TypeScript
alignRules(alignRule: LocalizedAlignRuleOptions): T
```

Sets the alignment rules in the relative container. This API is valid only when the container is RelativeContainer, This attribute replaces the original **left** and **right** directional parameters with **start** and **end** to support proper mirroring in right-to-left (RTL) layout modes. It is recommended that you use this attribute for configuring child component alignment rules in relative containers. This attribute supports dynamic configuration via [attributeModifier](#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignRule | [LocalizedAlignRuleOptions](arkts-arkui-common-comp-localizedalignruleoptions-i.md) | Yes | Alignment rules in the relative container. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## alignSelf

```TypeScript
alignSelf(value: ItemAlign): T
```

The alignment mode of the child component along the cross axis (the direction perpendicular to the main axis) of the parent container. After it is set, it overrides the alignItems setting of the parent container. This attribute is supported only by Flex, Column, Row, DynamicLayout, and GridRow containers.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ItemAlign](../arkts-apis/arkts-arkui-itemalign-e.md) | Yes | Alignment format of the child component on the cross axis of the parent container, which overrides the alignItems setting in the Flex, Column, Row, DynamicLayout, and GridRow layout containers. Use it when a child component needs a different alignment from other child components in the parent container (typical scenarios: most child components in the parent container are center-aligned, but a specific child component needs top or bottom alignment; or a special alignment needs to be specified for a single child component).<br>GridCol can bind the alignSelf attribute to change its own layout in the cross axis direction.<br>Default value: ItemAlign.Auto (indicates inheriting the alignment setting of the parent container) |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## allowDrop

```TypeScript
allowDrop(value: Array<UniformDataType>  | null | Array<string>): T
```

Sets the types of data that can be dropped to the component. If **allowDrop** is not set, the component accepts all data types by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[UniformDataType](arkts-arkui-common-comp-uniformdatatype-t.md)&gt; &#124; null &#124; Array&lt;string&gt; | Yes | Types of data that can be dropped to the component. Since API version 12, this parameter can be set to **null** to make the component reject all data types. Starting from API version 23, this parameter can be set to an application-defined data type string array Array&lt;string&gt; is supported. While there is no strict format requirement for the string, it should not duplicate the format of standard types in **UniformDataType**. You are advised to define them based on the principle of being easy to remember and distinguish.<br>**Since:** 23 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## allowForceDark

```TypeScript
allowForceDark(value: boolean): T
```

Set whether the component enables the ability to invert colors. This interface needs to be set as the first attribute of the component.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | value indicates whether the component enables the ability to invert colors. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## animation

```TypeScript
animation(value: AnimateParam): T
```

Sets a property animation for the component.

> **NOTE:** 
> 
> - When a single page contains a large number of components with animations, use [renderGroup](#rendergroup) to minimize frame freezing and improve animation performance. For best practices, see [Animation Usage Guide – Using RenderGroup](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-fair-use-animation#section1223162922415).
> 
> 
> - This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-common-comp-animateparam-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## aspectRatio

```TypeScript
aspectRatio(value: number): T
```

Sets the aspect ratio of the component, which can be obtained using the following formula: width/height. <br>- If only **width** and **aspectRatio** are set, the height is calculated using the following formula: width/aspectRatio. <br>- If only **height** and **aspectRatio** are set, the width is calculated using the following formula: height x aspectRatio. <br>- If **width**, **height**, and **aspectRatio** are set at the same time, the height is recalculated as width/aspectRatio, and the explicitly set height value does not take effect. <br>Applies to components that need to maintain a fixed aspect ratio, such as image display, video players, and maintaining proportions in responsive layouts. <br>After the **aspectRatio** attribute is set, the component's width and height are limited by the size of the parent component's content area. The maxWidth/maxHeight of [constraintSize](#constraintsize) takes precedence over **aspectRatio**. When the maxWidth/maxHeight constraints set by constraintSize conflict with the aspectRatio calculation result, the component follows the maxWidth/maxHeight constraints of constraintSize first, in which case aspectRatio may not take effect.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Specifies the aspect ratio of the current component. The value range is (0, +∞). <br>In API version 9 and earlier, the default value is **1.0**. <br>Since API version 10, there is no default value. <br>**NOTE:** <br> Use it when the aspect ratio of the component needs to be maintained (for example, when displaying images, videos, and other content that needs to maintain their ratio). <br>This attribute does not take effect when it is set to an invalid value (less than or equal to 0). Since API version 10, this attribute does not take effect when no value is set. <br>After this attribute is set, the width and height of the component are limited by the size of the parent component's content area, and the maxWidth/maxHeight of [constraintSize](#constraintsize) take precedence over aspectRatio. <br>For example, when **Row** has only the width set and no child components, if **aspectRatio** is not set or is a negative value, the height is 0. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<T>): T
```

Sets the attribute modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-common-comp-attributemodifier-i.md)&lt;T&gt; | Yes | The if/else syntax is supported. You need a custom class to implement the AttributeModifier API. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backdropBlur

```TypeScript
backdropBlur(value: number, options?: BlurOptions): T
```

Applies a background blur effect to the component. You can customize the blur radius and grayscale parameters.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Background blur effect to apply to the component. The input parameter is the blur radius. The larger the radius is, the more blurred the background is. If the value is **0**, the background is not blurred. |
| options | [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md) | No | Grayscale parameters.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backdropblur-1"></a>

## backdropBlur

```TypeScript
backdropBlur(radius: Optional<number>, options?: BlurOptions): T
```

Applies a background blur effect to the component. You can customize the blur radius and grayscale parameters. Compared to [backdropBlur](#backdropblur), the **radius** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Background blur effect to apply to the component. The input parameter is the blur radius. The larger the radius is, the more blurred the background is. If the value is **0**, the background is not blurred.<br>If **radius** is **undefined**, the background blur reverts to its default state (that is, no blur). |
| options | [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md) | No | Grayscale parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backdropblur-2"></a>

## backdropBlur

```TypeScript
backdropBlur(radius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T
```

Applies a background blur effect to the component. You can customize the blur radius and grayscale parameters. Compared with [backdropBlur&lt;sup&gt;18+&lt;/sup&gt;](#backdropblur-1), this API adds the **sysOptions** parameter, which allows for system adaptive adjustments.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Background blur effect to apply to the component. The input parameter is the blur radius. The larger the radius is, the more blurred the background is. If the value is **0**, the background is not blurred.<br>If **radius** is **undefined**, the background blur reverts to its default state (that is, no blur). |
| options | [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md) | No | Grayscale parameters. |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-common-comp-systemadaptiveoptions-i.md) | No | System adaptive adjustment options.<br>Default value: **{ disableSystemAdaptation: false }** |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## background

```TypeScript
background(content: CustomBuilder | ResourceColor, options?: BackgroundOptions): T
```

Add a background for the component.

Anonymous Object Rectification.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes |  |
| options | [BackgroundOptions](arkts-arkui-common-comp-backgroundoptions-i.md) | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle(value: BlurStyle, options?: BackgroundBlurStyleOptions): T
```

Defines the background material blur style. It encapsulates various blur radius, mask color, mask opacity, saturation, and brightness values through enum values.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md) | Yes | Settings of the background blur style, including the blur radius, mask color, mask opacity, saturation, and brightness. |
| options | [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md) | No | Background blur options.<br>This parameter cannot be used in ArkTS widgets. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backgroundblurstyle-1"></a>

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions): T
```

Defines the background material blur style. It encapsulates various blur radius, mask color, mask opacity, saturation, and brightness values through enum values. Compared to [backgroundBlurStyle&lt;sup&gt;9+&lt;/sup&gt;](#backgroundblurstyle), the **style** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes | Settings of the background blur style, including the blur radius, mask color, mask opacity, saturation, and brightness.<br>If **style** is **undefined**, the background blur reverts to its default state (that is, no blur). |
| options | [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md) | No | Background blur options.<br>This parameter cannot be used in ArkTS widgets. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backgroundblurstyle-2"></a>

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle(style: Optional<BlurStyle>, options?: BackgroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T
```

Defines the background material blur style. It encapsulates various blur radius, mask color, mask opacity, saturation, and brightness values through enum values. Compared with [backgroundBlurStyle&lt;sup&gt;18+&lt;/sup&gt;](#backgroundblurstyle-1), this API adds the **sysOptions** parameter, which allows for system adaptive adjustments.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes | Settings of the background blur style, including the blur radius, mask color, mask opacity, saturation, and brightness.<br>If **style** is **undefined**, the background blur reverts to its default state (that is, no blur). |
| options | [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md) | No | Background blur options.<br>This parameter cannot be used in ArkTS widgets. |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-common-comp-systemadaptiveoptions-i.md) | No | System adaptive adjustment options.<br>Default value: **{ disableSystemAdaptation: false }** |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## backgroundBrightness

```TypeScript
backgroundBrightness(params: BackgroundBrightnessOptions): T
```

Sets the background brightness of the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [BackgroundBrightnessOptions](arkts-arkui-common-comp-backgroundbrightnessoptions-i.md) | Yes | Parameters for setting the background brightness. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backgroundbrightness-1"></a>

## backgroundBrightness

```TypeScript
backgroundBrightness(options: Optional<BackgroundBrightnessOptions>): T
```

Sets the background brightness of the component. Compared to [backgroundBrightness&lt;sup&gt;12+&lt;/sup&gt;](#backgroundbrightness), the **options** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BackgroundBrightnessOptions](arkts-arkui-common-comp-backgroundbrightnessoptions-i.md)&gt; | Yes | Parameters for setting the background brightness.<br>If **options** is **undefined**, the background reverts to its default state with no brightness effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor): T
```

Background color

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="backgroundcolor-1"></a>

## backgroundColor

```TypeScript
backgroundColor(color: Optional<ResourceColor>): T
```

Background color

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="backgroundcolor-2"></a>

## backgroundColor

```TypeScript
backgroundColor(color: Optional<ResourceColor | ColorMetrics>): T
```

Background color

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; ColorMetrics&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backgroundEffect

```TypeScript
backgroundEffect(options: BackgroundEffectOptions): T
```

Sets the background effect of the component, including the blur radius, brightness, saturation, and color.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md) | Yes | Background effect of the component, including the blur radius, brightness, saturation, and color. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backgroundeffect-1"></a>

## backgroundEffect

```TypeScript
backgroundEffect(options: Optional<BackgroundEffectOptions>): T
```

Sets the background effect of the component, including the blur radius, brightness, saturation, and color. Compared to [backgroundEffect&lt;sup&gt;11+&lt;/sup&gt;](#backgroundeffect), the **options** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)&gt; | Yes | Background effect of the component, including the blur radius, brightness, saturation, and color.<br>If **options** is **undefined**, the background reverts to its default state with no effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="backgroundeffect-2"></a>

## backgroundEffect

```TypeScript
backgroundEffect(options: Optional<BackgroundEffectOptions>, sysOptions?: SystemAdaptiveOptions): T
```

Sets the background effect of the component, including the blur radius, brightness, saturation, and color. Compared with [backgroundEffect&lt;sup&gt;18+&lt;/sup&gt;](#backgroundeffect-1), this API adds the **sysOptions** parameter, which allows for system adaptive adjustments.

> **NOTE:** 
> 
> **backgroundEffect** performs real-time rendering per frame, resulting in high performance overhead. When the
> background blur effect remains unchanged, it is recommended that you use the static blur API
> [blur](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-effectkit-filter-i.md#blur). For best practices, see
> [Image Blurring Optimization – When to Use](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-fuzzy-scene-performance-optimization#section4945532519).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md)&gt; | Yes | Background effect of the component, including the blur radius, brightness, saturation, and color.<br>If **options** is **undefined**, the background reverts to its default state with no effect. |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-common-comp-systemadaptiveoptions-i.md) | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## backgroundFilter

```TypeScript
backgroundFilter(filter: Filter): T
```

Sets the visual effect of the background filter.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [Filter](arkts-arkui-common-comp-filter-t.md) | Yes | Visual effect of the background filter. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## backgroundImage

```TypeScript
backgroundImage(src: ResourceStr | PixelMap, repeat?: ImageRepeat): T
```

Background image src: Image address url

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes |  |
| repeat | [ImageRepeat](../arkts-apis/arkts-arkui-imagerepeat-e.md) | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="backgroundimage-1"></a>

## backgroundImage

```TypeScript
backgroundImage(src: ResourceStr | PixelMap, options?: BackgroundImageOptions): T
```

Background image

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | the background image source |
| options | [BackgroundImageOptions](arkts-arkui-common-comp-backgroundimageoptions-i.md) | No | config the options |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backgroundImagePosition

```TypeScript
backgroundImagePosition(value: Position | Alignment): T
```

Background image position x:Horizontal coordinate;y:Vertical axis coordinate.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position &#124; [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backgroundImageResizable

```TypeScript
backgroundImageResizable(value: ResizableOptions): T
```

Background image resizable. value:resizable options

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) | Yes | Indicates the resizable options. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## backgroundImageSize

```TypeScript
backgroundImageSize(value: SizeOptions | ImageSize): T
```

Background image size

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) &#124; [ImageSize](../arkts-apis/arkts-arkui-imagesize-e.md) | Yes | The width and height of the background image. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindContentCover

```TypeScript
bindContentCover(isShow: boolean, builder: CustomBuilder, type?: ModalTransition): T
```

Binds a full-screen modal to the component, which can be displayed when the component is touched. The content of the modal is customizable. The transition type can be set to none, slide-up and slide-down animation, and opacity gradient animation.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShow | boolean | Yes | Whether to display the full-screen modal.<br>- **true**: Display the modal.<br>- **false**: Hide the modal.<br>Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).<br>Since API version 18, this attribute supports two -way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters). |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the modal. The root node in **builder** must be unique. |
| type | [ModalTransition](arkts-arkui-common-comp-modaltransition-e.md) | No | System transition mode of the modal.<br> Default value: **ModalTransition.DEFAULT**.<br>**NOTE:** <br> This property has no effect when it is set together with **transition**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="bindcontentcover-1"></a>

## bindContentCover

```TypeScript
bindContentCover(isShow: boolean, builder: CustomBuilder, options?: ContentCoverOptions): T
```

Binds a full-screen modal to the component, which can be displayed when the component is touched. The modal page content and transition mode are configurable.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShow | boolean | Yes | Whether to display the full-screen modal.<br>- **true**: Display the modal.<br>- **false**: Hide the modal.<br>Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).<br>Since API version 18, this attribute supports two -way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters). |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the modal. |
| options | [ContentCoverOptions](arkts-arkui-common-comp-contentcoveroptions-i.md) | No | Optional attributes of the modal. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## bindContextMenu

```TypeScript
bindContextMenu(content: CustomBuilder, responseType: ResponseType, options?: ContextMenuOptions): T
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Indicates the content of context menu. |
| responseType | [ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md) | Yes | Indicates response type of context menu, Long pressing with a mouse device is not supported. |
| options | [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md) | No | Indicates the options of context menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="bindcontextmenu-1"></a>

## bindContextMenu

```TypeScript
bindContextMenu(isShown: boolean, content: CustomBuilder, options?: ContextMenuOptions): T
```

Binds a context menu to the component, whose visibility is subject to the isShown settings.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShown | boolean | Yes | true means display content, false means hide content, default is false. <p>&lt;strong&gt;NOTE&lt;/strong&gt;:<br>The menu can be displayed properly only when the related page has been constructed. If this parameter is set to true before the construction is complete, display issues, such as misplacement, distortion, or failure to pop up, may occur. To trigger dragging by long presses is not supported. </p> |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Indicates the content of context menu. |
| options | [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md) | No | Indicates the options of context menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindContextMenuByIsShow

```TypeScript
bindContextMenuByIsShow(isShow: boolean, content: CustomBuilder | Array<MenuElement>, options?: ContextMenuOptions): T
```

Binds a context menu to the component, whose visibility is subject to the isShow settings.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShow | boolean | Yes | true means display content, false means hide content, default is false. <p>&lt;strong&gt;NOTE&lt;/strong&gt;:<br>The menu can be displayed properly only when the related page has been constructed. If this parameter is set to true before the construction is complete, display issues, such as misplacement, distortion, or failure to pop up, may occur. Dragging via long press is not supported. </p>. |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt; | Yes | Indicates the content of context menu. |
| options | [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md) | No | Indicates the options of context menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindContextMenuByResponseType

```TypeScript
bindContextMenuByResponseType(content: CustomBuilder | Array<MenuElement>, responseType: ResponseType,
      options?: ContextMenuOptions): T
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Custom or fixed-style menu items are supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt; | Yes | Indicates the content of context menu. |
| responseType | [ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md) | Yes | Indicates response type of context menu. Long pressing with a mouse device is not supported. |
| options | [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md) | No | Indicates the options of context menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindContextMenuWithResponse

```TypeScript
bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | undefined, options?: ContextMenuOptions): T
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Only custom menu items are supported. Long pressing with a mouse device is not supported.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [CustomBuilderT](arkts-arkui-common-comp-custombuildert-t.md)&lt;[ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md)&gt; &#124; undefined | Yes | Indicates the content of context menu. Undefined means unbinding. |
| options | [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md) | No | Indicates the options of context menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="bindcontextmenuwithresponse-1"></a>

## bindContextMenuWithResponse

```TypeScript
bindContextMenuWithResponse(content: CustomBuilderT<ResponseType> | Array<MenuElement> | undefined,
    options?: ContextMenuOptions): T
```

Binds a context menu to this component, which is displayed when the user long-presses or right-clicks the component. Custom or fixed-style menu items are supported. Long pressing with a mouse device is not supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | [CustomBuilderT](arkts-arkui-common-comp-custombuildert-t.md)&lt;[ResponseType](../arkts-apis/arkts-arkui-responsetype-e.md)&gt; &#124; Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt; &#124; undefined | Yes | Indicates the content of context menu. Undefined means unbinding. |
| options | [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md) | No | Indicates the options of context menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindMenu

```TypeScript
bindMenu(content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T
```

Menu control

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt; &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Indicates the content of menu.<br>**Since:** 11 |
| options | [MenuOptions](arkts-arkui-common-comp-menuoptions-i.md) | No | Indicates the options of menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="bindmenu-1"></a>

## bindMenu

```TypeScript
bindMenu(isShow: boolean, content: Array<MenuElement> | CustomBuilder, options?: MenuOptions): T
```

Menu control

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShow | boolean | Yes | true means display menu, false means hide menu, default is false. |
| content | Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt; &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Indicates the content of menu. |
| options | [MenuOptions](arkts-arkui-common-comp-menuoptions-i.md) | No | Indicates the options of menu. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindPopup

```TypeScript
bindPopup(show: boolean, popup: PopupOptions | CustomPopupOptions): T
```

Popup control <p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>The popup can be displayed only after the entire page is fully constructed. Therefore, to avoid incorrect display positions and shapes, do not set this parameter to true while the page is still being constructed. </p>

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes |  |
| popup | [PopupOptions](arkts-arkui-common-comp-popupoptions-i.md) &#124; [CustomPopupOptions](arkts-arkui-common-comp-custompopupoptions-i.md) | Yes | <br>**Since:** 8 |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## bindSheet

```TypeScript
bindSheet(isShow: boolean, builder: CustomBuilder, options?: SheetOptions): T
```

Binds a sheet to the component, which is displayed when the component is touched.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isShow | boolean | Yes | Whether to display the sheet.<br>**true**: Display the sheet.<br>**false**: Hide the sheet.<br>Since API version 10, this parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).<br>Since API version 18, this attribute supports two -way binding through [!!](../../../ui/state-management/arkts-new-binding.md). |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes | Content of the sheet. |
| options | [SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md) | No | Optional attributes of the sheet. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## bindTips

```TypeScript
bindTips(message: TipsMessageType, options?: TipsOptions): T
```

Tips control

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [TipsMessageType](arkts-arkui-common-comp-tipsmessagetype-t.md) | Yes |  |
| options | [TipsOptions](arkts-arkui-common-comp-tipsoptions-i.md) | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## blendMode

```TypeScript
blendMode(value: BlendMode, type?: BlendApplyType): T
```

Defines how the component's content (including the content of it child components) is blended with the existing content on the canvas (possibly offscreen canvas) below.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BlendMode](arkts-arkui-common-comp-blendmode-e.md) | Yes | Blend mode.<br>Default value: **BlendMode.NONE**<br>**NOTE:** <br>When **BlendMode.NONE** is used, the blend effect is **BlendMode.SRC_OVER** by default, and **BlendApplyType** does not take effect. |
| type | [BlendApplyType](arkts-arkui-common-comp-blendapplytype-e.md) | No | Whether the blend mode is implemented offscreen.<br>Default value: **BlendApplyType.FAST**<br>**NOTE:** <br>1. **BlendApplyType.FAST**: The blend mode is not implemented offscreen. <br>2. **BlendApplyType.OFFSCREEN**: An offscreen canvas of the size of the current component is created. The content of the current component (including child components) is then drawn onto the offscreen canvas, and blended with the existing content on the canvas below using the specified blend mode. This approach may cause issues with screen capture for APIs such as [linearGradientBlur&lt;sup&gt;12+&lt;/sup&gt;](#lineargradientblur), [backgroundEffect](#backgroundeffect), [brightness](#brightness), and [blur](#blur). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="blendmode-1"></a>

## blendMode

```TypeScript
blendMode(mode: Optional<BlendMode>, type?: BlendApplyType): T
```

Defines how the component's content (including the content of it child components) is blended with the existing content on the canvas (possibly offscreen canvas) below. Compared to [blendMode&lt;sup&gt;11+&lt;/sup&gt;](#blendmode), the **mode** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlendMode](arkts-arkui-common-comp-blendmode-e.md)&gt; | Yes | Blend mode.<br>Default value: **BlendMode.NONE**<br>If **mode** is **undefined**, the component reverts to its original effect of not enabling offscreen rendering as a whole before blending with the parent component.<br>**NOTE:** <br>When **BlendMode.NONE** is used, the blend effect is **BlendMode.SRC_OVER** by default, and **BlendApplyType** does not take effect. |
| type | [BlendApplyType](arkts-arkui-common-comp-blendapplytype-e.md) | No | Whether the blend mode is implemented offscreen.<br>Default value: **BlendApplyType.FAST**<br>**NOTE:** <br>1. **BlendApplyType.FAST**: The blend mode is not implemented offscreen. <br>2. **BlendApplyType.OFFSCREEN**: An offscreen canvas of the size of the current component is created. The content of the current component (including child components) is then drawn onto the offscreen canvas, and blended with the existing content on the canvas below using the specified blend mode. This approach may cause issues with screen capture for APIs such as [linearGradientBlur&lt;sup&gt;12+&lt;/sup&gt;](#lineargradientblur), [backgroundEffect](#backgroundeffect), [brightness](#brightness), and [blur](#blur). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## blur

```TypeScript
blur(value: number, options?: BlurOptions): T
```

Applies a foreground blur effect to the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Foreground blur effect to apply to the component. The input parameter is the blur radius. The larger the radius is, the more blurred the content is. If the value is **0**, the content is not blurred. |
| options | [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md) | No | Grayscale parameters.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="blur-1"></a>

## blur

```TypeScript
blur(blurRadius: Optional<number>, options?: BlurOptions): T
```

Applies a foreground blur effect to the component. Compared to [blur](#blur), the **blurRadius** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Foreground blur effect to apply to the component. The input parameter is the blur radius. The larger the radius is, the more blurred the content is. If the value is **0**, the content is not blurred.<br>If **blurRadius** is set to **undefined**, the previous value is retained. |
| options | [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md) | No | Grayscale parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="blur-2"></a>

## blur

```TypeScript
blur(blurRadius: Optional<number>, options?: BlurOptions, sysOptions?: SystemAdaptiveOptions): T
```

Applies a foreground blur effect to the component. Compared to [blur&lt;sup&gt;18+&lt;/sup&gt;](#blur-1), this API adds the **sysOptions** parameter, which allows for system adaptive adjustments.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Foreground blur effect to apply to the component. The input parameter is the blur radius. The larger the radius is, the more blurred the content is. If the value is **0**, the content is not blurred.<br>If **blurRadius** is set to **undefined**, the previous value is retained. |
| options | [BlurOptions](arkts-arkui-common-comp-bluroptions-i.md) | No | Grayscale parameters. |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-common-comp-systemadaptiveoptions-i.md) | No | System adaptive adjustment options.<br>Default value: **{ disableSystemAdaptation: false }** |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## border

```TypeScript
border(value: BorderOptions): T
```

Sets the border.  
> **NOTE:** 
> 
> When neither **color** nor **radius** is specified, set borderColor and borderRadius after
> border to ensure they take effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BorderOptions](../arkts-apis/arkts-arkui-borderoptions-i.md) | Yes | Unified border style setting API.<br>The default border width is **0**, that is, no border is displayed.<br>The default border corner radius is **0**, that is, no corner radius is displayed.<br>The default border color is Color.Black.<br>Since API version 9, the border of the parent node is displayed above the content of the child node.<br>When color and radius are not set, to ensure that borderColor and borderRadius take effect, set borderColor and borderRadius after border. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## borderColor

```TypeScript
borderColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T
```

Sets the border color.  
> **NOTE:** <br>When using border for unified setting of the border and the color parameter is omitted, borderColor must be called after border to take effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](../arkts-apis/arkts-arkui-localizededgecolors-i.md) | Yes | Sets the border color of the element. After setting, the border is displayed in the corresponding color.<br>Default value: **Color.Black**<br>**Note:** When using the LocalizedEdgeColors type, the border color settings differ under different language directions. See Example 2. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## borderImage

```TypeScript
borderImage(value: BorderImageOption): T
```

Sets the border image of the component.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BorderImageOption](arkts-arkui-common-comp-borderimageoption-i.md) | Yes | Border image or border gradient. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## borderRadius

```TypeScript
borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses): T
```

Sets the border radius.  
> **NOTE:** <br>When using border for unified setting of the border and the radius parameter is omitted, borderRadius must be called after border to take effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md) | Yes | Element border corner radius. Percentage is supported, and the percentage is based on the component width. Default unit: vp.<br>Default value: **0**. After the corner radius is set, you can use the [clip](#clip) attribute to clip the component so that child components do not exceed the component itself.<br>**NOTE:** <br>When the LocalizedBorderRadiuses type is used, the border corner radius settings differ under different language directions. See Also example 2.<br>Set four different corner radii. If a corner radius exceeds half of the smaller value between the height and the width, the irregular corner radius is drawn differently by value ratio. See example 4 for the effect.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="borderradius-1"></a>

## borderRadius

```TypeScript
borderRadius(value: Length | BorderRadiuses | LocalizedBorderRadiuses, type?: RenderStrategy): T
```

Sets the border corner radius and the rendering strategy for rounded corners.  
> **NOTE:** <br>When using border for unified setting of the border and the radius parameter is omitted, borderRadius must be called after border to take effect.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md) &#124; [LocalizedBorderRadiuses](../arkts-apis/arkts-arkui-localizedborderradiuses-i.md) | Yes | Set the border corner radius of the element. Percentage is supported, and the percentage is based on the component width. Default you can use the [clip](#clip) attribute to clip the component so that child components do not exceed the component itself.<br> **Note:** When using the LocalizedBorderRadiuses type, the border corner radius settings differ under different language directions. See also example 2.<br>Set four different corner radius values. If a corner radius value exceeds half of the smaller value of the height and width, the irregular corner radius is drawn differently by value ratio. See example 4 for the effect. <br>Unit: vp.<br>After the corner radius is set. Default value: **0**. |
| type | [RenderStrategy](../arkts-apis/arkts-arkui-renderstrategy-e.md) | No | Sets the mode for drawing the corner radius of the component.<br><br>Optional values:<br>- **RenderStrategy.FAST**: fast rendering mode, suitable for common corner radius scenarios with better performance. If the component contains complex visual effects such as blur, using this mode may cause abnormal corner radius clipping.<br>- **RenderStrategy.OFFSCREEN**: offscreen rendering mode, suitable for corner radius scenarios with complex visual effects such as blur. It can render the corner radius correctly but incurs higher performance overhead. <br>Default value: **RenderStrategy.FAST**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## borderStyle

```TypeScript
borderStyle(value: BorderStyle | EdgeStyles): T
```

Sets the border style.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BorderStyle](../arkts-apis/arkts-arkui-borderstyle-e.md) &#124; EdgeStyles | Yes | Element border style.<br>Default value: **BorderStyle.Solid**<br>**Since:** 9 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## borderWidth

```TypeScript
borderWidth(value: Length | EdgeWidths | LocalizedEdgeWidths): T
```

Sets the border width.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; EdgeWidths &#124; [LocalizedEdgeWidths](../arkts-apis/arkts-arkui-localizededgewidths-i.md) | Yes | Sets the border width of the element. Percentage is not supported. Default unit: vp.<br>Default value: **0**.<br>**Note:** When the LocalizedEdgeWidths type is used, the border width setting differs under different language directions. See Example 2.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## brightness

```TypeScript
brightness(value: number): T
```

Applies a brightness effect to the component. If this API is not used, there will be no change by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Brightness effect of the component. **1**: No brightness adjustment. Less than 1.0: decreases brightness. 0 or less: Complete black. Greater than 1: increases brightness. 2 or greater: complete white.<br>Value range: [0, +∞)<br>Recommended value range: [0, 2]<br>**NOTE:** <br>A value less than 0 evaluates to the value **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="brightness-1"></a>

## brightness

```TypeScript
brightness(brightness: Optional<number>): T
```

Applies a brightness effect to the component. If this API is not used, there will be no change by default. Compared with [brightness](#brightness), this API supports the **undefined** type for the **brightness** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Brightness effect of the component. **1**: No brightness adjustment. Less than 1.0: decreases brightness. 0 or less: Complete black. Greater than 1: increases brightness. 2 or greater: complete white.<br>Value range: [0, +∞)<br>Recommended value range: [0, 2]<br>**NOTE:** <br>A value less than 0 evaluates to the value **0**.<br>If **brightness** is **undefined**, the brightness level is reset to **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## chainMode

```TypeScript
chainMode(direction: Axis, style: ChainStyle): T
```

Sets the parameters of the chain in which the component is the head. This attribute takes effect only when the parent container is RelativeContainer. The chain head is the first component in the chain that satisfies the chain formation rules. In a horizontal layout, it starts from the left (or from the right in a mirrored language layout). In a vertical layout, it starts from the top.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [Axis](../arkts-apis/arkts-arkui-axis-e.md) | Yes | indicates direction of the chain |
| style | [ChainStyle](arkts-arkui-common-comp-chainstyle-e.md) | Yes | indicates style of the chain |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## chainWeight

```TypeScript
chainWeight(chainWeight: ChainWeightOptions): T
```

Sets the weight of the component in a chain, which is used to re-lay out components that form the chain. This attribute takes effect only when the parent container is RelativeContainer.

**NOTE:** 

Since API version 23, dynamic configuration via [attributeModifier](#attributemodifier) is supported

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chainWeight | [ChainWeightOptions](../arkts-apis/arkts-arkui-chainweightoptions-i.md) | Yes | Layout weight of the component in the horizontal or vertical direction. The component with **chainWeight** set will have its size in the horizontal or vertical direction allocated according to the set weights. The allocation ignores the component's intrinsic size and enables the component to adaptively fill the remaining space. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## clickEffect

```TypeScript
clickEffect(value: ClickEffect | null): T
```

Sets the click feedback effect of the component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ClickEffect](arkts-arkui-common-comp-clickeffect-i.md) &#124; null | Yes | Click feedback effect of the component.<br>**NOTE:** <br>Use **null** to disable the click feedback effect.<br>Avoid using this feature in scenarios where the component size dynamically changes.<br>This attribute is not supported when the component cannot trigger universal events.<br> After the click feedback effect triggers scaling, the touch point may fall outside the control, making the component unresponsive to gesture events. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="clickeffect-1"></a>

## clickEffect

```TypeScript
clickEffect(effect: Optional<ClickEffect | null>): T
```

Sets the click feedback effect of the component. Compared with [clickEffect](#clickeffect), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ClickEffect](arkts-arkui-common-comp-clickeffect-i.md) &#124; null&gt; | Yes | Click feedback effect of the component.<br>**NOTE:** <br>Use **undefined** or **null** to disable the click feedback effect.<br>Avoid using this feature in scenarios where the component size dynamically changes.<br>This attribute is not supported when the component cannot trigger universal events.<br>After the click feedback effect triggers scaling, the touch point may fall outside the control, making the component unresponsive to gesture events. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## clip

```TypeScript
clip(value: boolean): T
```

Sets whether to clip the areas of child components that extend beyond this component's bounds, that is, whether to perform clipping based on the edge contour of the parent container If this API is not used, the area of child components extending beyond the current component's bounds is not clipped by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to clip the areas of child components that extend beyond the current component's bounds.<br>The value **true** means to clip the areas of child components that extend beyond the current component's bounds, and **false** means the opposite.<br>Note: If this parameter is set to **true**, child components exceeding the current component's bounds will not respond to bound gesture events. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="clip-1"></a>

## clip

```TypeScript
clip(clip: Optional<boolean>): T
```

Sets whether to clip the areas of child components that extend beyond this component's bounds, that is, whether to perform clipping based on the edge contour of the parent container If this API is not used, the area of child components extending beyond the current component's bounds is not clipped by default. Compared with [clip&lt;sup&gt;12+&lt;/sup&gt;](#clip), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clip | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to clip the areas of child components that extend beyond the current component's bounds.<br>Note: If this parameter is set to **true**, child components exceeding the current component's bounds will not respond to bound gesture events.<br>If **clip** is set to **undefined**, clipping is disabled, and child components are not clipped. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="clip-2"></a>

## clip

```TypeScript
clip(value: boolean | CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute): T
```

Sets whether to clip this component based on the given shape.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** [clipShape](#clipshape)

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; [CircleAttribute](arkts-arkui-circle-comp-attribute.md) &#124; [EllipseAttribute](arkts-arkui-ellipse-comp-attribute.md) &#124; [PathAttribute](arkts-arkui-path-comp-attribute.md) &#124; [RectAttribute](arkts-arkui-rect-comp-attribute.md) | Yes | Clip mode. If the value is a shape attribute, the component is clipped based on the specified shape. If the value is of the Boolean type, it specifies whether to clip the component based on the boundaries of the parent container.<br> Default value: **false**.<br>Note: If the value is a shape attribute, the clipped area can still respond to bound gesture events. If the value is of the Boolean type, the clipped area will not respond to bound gesture events. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## clipShape

```TypeScript
clipShape(value: CircleShape | EllipseShape | PathShape | RectShape): T
```

Clips this component according to the specified shape (which may include position information).

> **NOTE:** 
> 
> Different shapes support different ranges of attributes. A path is one type of shape, along with others like
> ellipses and rectangles.
> 
> Path shapes do not support setting width and height attributes. For details about the supported attributes, see
> the specific shape documentation.
> 
> The [fill](../arkts-apis/arkts-arkui-arkui-shape-commonshapemethod-c.md#fill) attribute of shapes has no effect on the **clipShape**
> API.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CircleShape](arkts-arkui-common-comp-circleshape-t.md) &#124; [EllipseShape](arkts-arkui-common-comp-ellipseshape-t.md) &#124; [PathShape](arkts-arkui-common-comp-pathshape-t.md) &#124; [RectShape](arkts-arkui-common-comp-rectshape-t.md) | Yes | Shape (which may include position information) to clip the current component.<br>Note: The clipped area remains responsive to bound gesture events. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="clipshape-1"></a>

## clipShape

```TypeScript
clipShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T
```

Clips this component according to the specified shape (which may include position information). Compared with [clipShape&lt;sup&gt;12+&lt;/sup&gt;](#clipshape), this API supports the **undefined** type.

> **NOTE:** 
> 
> Different shapes support different ranges of attributes. A path is one type of shape, along with others like
> ellipses and rectangles.
> 
> Path shapes do not support setting width and height attributes. For details about the supported attributes, see
> the specific shape documentation.
> 
> The [fill](../arkts-apis/arkts-arkui-arkui-shape-commonshapemethod-c.md#fill) attribute of shapes has no effect on the **clipShape**
> API.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CircleShape](arkts-arkui-common-comp-circleshape-t.md) &#124; [EllipseShape](arkts-arkui-common-comp-ellipseshape-t.md) &#124; [PathShape](arkts-arkui-common-comp-pathshape-t.md) &#124; [RectShape](arkts-arkui-common-comp-rectshape-t.md)&gt; | Yes | Shape (which may include position information) to clip the current component.<br>Note: The clipped area remains responsive to bound gesture events.<br>If the value of **shape** is **undefined**, the current setting will be reset to its default state. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## colorBlend

```TypeScript
colorBlend(value: Color | string | Resource): T
```

Applies a color blend effect to the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Color to blend with the component. The value can be a string, for example, **'0x000000'** or **'rgba(0,0,0,1)'**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="colorblend-1"></a>

## colorBlend

```TypeScript
colorBlend(color: Optional<Color | string | Resource>): T
```

Applies a color blend effect to the component. Compared with [colorBlend](#colorblend), this API supports the **undefined** type for the **color** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Color](../arkts-apis/arkts-arkui-color-e.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Color to blend with the component. The value can be a string, for example, **'0x000000'** or **'rgba(0,0,0,1)'**.<br>If **color** is **undefined**, the component reverts to its original effect with no color blending. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## compositingFilter

```TypeScript
compositingFilter(filter: Filter): T
```

Sets the visual effect of the compositing filter.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [Filter](arkts-arkui-common-comp-filter-t.md) | Yes | Visual effect of the compositing filter. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## constraintSize

```TypeScript
constraintSize(value: ConstraintSizeOptions): T
```

Sets the constraint size, which limits the size range during component layout. After the setting, the width and height of the component are limited to the specified minimum and maximum values. The priority of **constraintSize** is higher than that of the **width** and **height** attributes. <br>Since API version 10, this API supports the calc calculation feature.

**Impact of constraintSize(minWidth/maxWidth/minHeight/maxHeight) on width/height**

| Default Value | Result |  
| ---------------------------------------- | ---------------------------------------- |  
| \ | width=MAX(minWidth,MIN(maxWidth,width))<br>height=MAX(minHeight,MIN(maxHeight,height)) |
| maxWidth, maxHeight| width=MAX(minWidth,width)<br>height=MAX(minHeight,height)  
| minWidth, minHeight| width=MIN(maxWidth,width)<br>height=MIN(maxHeight,height) |  
| width, height| If minWidth &lt; maxWidth, the layout logic of the component takes effect, and the value range of  
**width** is [minWidth, maxWidth]. Otherwise, width = MAX(minWidth, maxWidth).<br>If minHeight &lt; maxHeight, the layout logic of the component takes effect, and the value range of **height** is [minHeight, maxHeight]. Otherwise, height = MAX (minHeight, maxHeight).|

| width and maxWidth; height and maxHeight| width = minWidth<br>height = minHeight |  
| width and minWidth; and height and minHeight| The layout logic of the component takes effect, and the value of  
**width** cannot be greater than that of **maxWidth**.<br>The layout logic of the component takes effect, and the value of **height** cannot be greater than that of **maxHeight**.|

| minWidth and maxWidth; minHeight and maxHeight| The width of the component is initially determined by the value of **width**, and it may be adjusted based on other layout attributes.<br>The height of the component is initially determined by the value of **height**, and it may be adjusted based on other layout attributes.|

| width, minWidth, and maxWidth| The layout restrictions passed by the parent container are used for layout.|  
| height, minHeight, and maxHeight| The layout restrictions passed by the parent container are used for layout.|

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint size. The priority of **constraintSize** is higher than that of [width](#width) and [height](#height). For the value result, refer to the impact of the **constraintSize** value on width and height. <br>Default value:<br>**{<br>minWidth:&nbsp;0,<br>maxWidth:&nbsp;Infinity,<br>minHeight:&nbsp;0, <br>maxHeight:&nbsp;Infinity<br>}**<br>Abnormal value: For a string starting with a number, only the numeric part is parsed; for a string not starting with a number, it is parsed as 0. For other abnormal values, the **constraintSize** attribute is restored to the default behavior when it is not configured. <br>Unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## contrast

```TypeScript
contrast(value: number): T
```

Applies a contrast effect to the component. If this API is not used, there will be no change by default.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Contrast of the component. The input parameter is a contrast value. If the value is **1**, the source image is displayed. If the value is greater than 1, a larger value indicates a higher contrast and a clearer image. If the value is less than 1, a smaller value indicates a lower contrast is. If the value is **0**, the image becomes all gray.<br>Recommended value range: [0, 10)<br>**NOTE:** <br>A value less than 0 evaluates to the value **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="contrast-1"></a>

## contrast

```TypeScript
contrast(contrast: Optional<number>): T
```

Applies a contrast effect to the component. If this API is not used, there will be no change by default. Compared to [contrast](#contrast), the **contrast** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contrast | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Contrast of the component. The input parameter is a contrast value. If the value is **1**, the source image is displayed. If the value is greater than 1, a larger value indicates a higher contrast and a clearer image. If the value is less than 1, a smaller value indicates a lower contrast is. If the value is **0**, the image becomes all gray.<br>Recommended value range: [0, 10)<br>**NOTE:** <br>A value less than 0 evaluates to the value **0**.<br>If **contrast** is **undefined**, the contrast effect is reset to **1.0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## customProperty

```TypeScript
customProperty(name: string, value: Optional<Object>): T
```

Sets a custom property for this component.

In versions earlier than API 26.0.0, [custom components](../../../ui/state-management/arkts-create-custom-components.md) do not support custom properties.

Since API 26.0.0, custom components support setting and reading custom properties.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the custom property. |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Object&gt; | Yes | Value of the custom property. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## defaultFocus

```TypeScript
defaultFocus(value: boolean): T
```

Specifies whether to set this component as the default focus of the current [hierarchical page](../../../ui/arkts-common-events-focus-event.md#basic-concepts). If **defaultFocus** is not set, the component will not receive initial focus on the current page.

> **NOTE:** 
> 
> This setting applies to pages that support routing or modal-type container components, such as **Page**,
> **NaviDestination**, **NavBar**, **PopUp**, and **Dialog**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to set the component as the default focus of the current [hierarchical page](../../../ui/arkts-common-events-focus-event.md#basic-concepts). This parameter takes effect only when the hierarchical page is new and accessed for the first time.<br>**NOTE:** <br>The value **true** means to set the component as the default focus, and the value **false** has no effect.<br>If no component on the hierarchical page has **defaultFocus(true)** set:<br>For API version 11 and earlier, the default focus is on the first focusable non-container component.<br>For API version versions later than 11, the default focus is on the hierarchical page's root container.<br>If **defaultFocus(true)** is set for multiple components on the hierarchical page, the first component found in the component tree depth-first traversal is used as the default focus. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## direction

```TypeScript
direction(value: Direction): T
```

Sets the layout along the main axis within the component's drawing area. This attribute can be dynamically set using [attributeModifier](#attributemodifier).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Direction](../arkts-apis/arkts-arkui-direction-e.md) | Yes | Sets the layout along the main axis within the drawing region of the current component.<br>When the attribute is set to **auto**, the layout follows the system language direction. <br>This attribute does not take effect on the **Column** component. <br>Default value: **Direction.Auto** <br>When **direction** is **undefined** or **null**, the default value is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## displayPriority

```TypeScript
displayPriority(value: number): T
```

Sets the display priority of the current component in a Row/Column/Flex (single-line) container. The priority is determined by the integer part of the value, and a larger integer part indicates a higher priority. <br>Applies to scenarios where child components are dynamically shown or hidden based on the parent container space in responsive layouts. For example, important content is displayed first and secondary content is hidden on different screen sizes.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Sets the display priority of the current component in the layout container. The value range is 0, +∞).<br>Default value: **1** <br>**NOTE:** <br> Takes effect only in [Row/Column/Flex (single-line) container components. <br>Used when the container space is limited and the display order of components needs to be controlled or low-priority components need to be hidden (for example, dynamically displaying content based on the available space in a Flex container). It is recommended to set the priority based on the importance of the component, with a larger value (such as 2-10) for key components and a smaller value (such as 1) for secondary components. <br>The digits after the decimal point do not affect the priority. All values not greater than 1 have the same priority. When the value is greater than 1, the larger the integer part of displayPriority, the higher the priority; values within the same integer range have the same priority. For example, **0.5** and **1.0** have the same priority (both are not greater than 1); **1.5** and **1.9** have the same priority (both have an integer part of 1); **2.0** and **2.9** have the same priority (both have an integer part of 2), and their priority is higher than that of 1.x. <br>If the parent container has insufficient space, child components with lower priority are hidden. If child components at a certain priority level are hidden, all child components with lower priority are also hidden. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## doubleSided

```TypeScript
doubleSided(value: Optional<boolean>): T
```

Sets whether to component is double-sided.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to draw both sides of component. **true**: Both front and back sides are visible (default). **false**: Only to front side is visible, to back side is hidden when rotated. When **value** is **undefined**, the component reverts to default double-sided setting (**true**). |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## draggable

```TypeScript
draggable(value: boolean): T
```

Sets whether the component is draggable. By default, the component is not draggable.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the component is draggable.<br>**true**: The component is draggable.<br> **false**: The component is not draggable. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## dragPreview

```TypeScript
dragPreview(value: CustomBuilder | DragItemInfo | string): T
```

Sets the preview image displayed during component drag operations.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](arkts-arkui-common-comp-dragiteminfo-i.md) &#124; string | Yes | Preview image displayed during component drag operations. It only applies to [onDragStart](#ondragstart) drag mode.<br>If the component supports drag and drop and a preview is specified through [bindContextMenu](#bindcontextmenu), that specified preview is displayed when the component is dragged. The priority of the background image returned in [onDragStart](#ondragstart) is lower than that of the preview set in [dragPreview](#dragpreview). This means that, once set, the latter will be used in place of the former. Using [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8) requires offline rendering and may increase performance overhead and latency. In light of this, you are advised to use [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) in [DragItemInfo](arkts-arkui-common-comp-dragiteminfo-i.md) instead.<br> When an ID of the string type is passed in, the snapshot of the component assigned the ID is used as the preview image. If the component assigned the ID cannot be found or its Visibility attribute is set to **None** or **Hidden**, a snapshot of the current component is used as the preview image. Currently, snapshots do not support visual effects, such as brightness, shadow, blur, and rotation.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="dragpreview-1"></a>

## dragPreview

```TypeScript
dragPreview(preview: CustomBuilder | DragItemInfo | string, config?: PreviewConfiguration): T
```

Sets the drag preview for the component. This API specifically configures or disables the lift animation effect.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| preview | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [DragItemInfo](arkts-arkui-common-comp-dragiteminfo-i.md) &#124; string | Yes | Preview image displayed during component drag operations. It only applies to [onDragStart](#ondragstart) drag mode.<br>If the component supports drag and drop and a preview is specified through [bindContextMenu](#bindcontextmenu), that specified preview is displayed when the component is dragged. The priority of the background image returned in [onDragStart](#ondragstart) is lower than that of the preview set in [dragPreview](#dragpreview). This means that, once set, the latter will be used in place of the former. Using [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8) requires offline rendering and may increase performance overhead and latency. In light of this, you are advised to use [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) in [DragItemInfo](arkts-arkui-common-comp-dragiteminfo-i.md) instead.<br> When an ID of the string type is passed in, the snapshot of the component assigned the ID is used as the preview image. If the component assigned the ID cannot be found or its Visibility attribute is set to **None** or **Hidden**, a snapshot of the current component is used as the preview image. Currently, snapshots do not support visual effects, such as brightness, shadow, blur, and rotation. |
| config | [PreviewConfiguration](arkts-arkui-common-comp-previewconfiguration-i.md) | No | Additional settings for the drag preview.<br>This parameter is effective only for previews set using [dragPreview](#dragpreview). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## dragPreviewOptions

```TypeScript
dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T
```

Sets the preview image processing mode, badge count, and interaction behavior during drag operations. The **onItemDragStart** drag mode is not supported.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DragPreviewOptions](arkts-arkui-common-comp-dragpreviewoptions-i.md) | Yes | Preview image processing mode and badge count during dragging. |
| options | [DragInteractionOptions](arkts-arkui-common-comp-draginteractionoptions-i.md) | No | Interaction behavior for the floating preview image.<br>Default value: empty<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## drawModifier

```TypeScript
drawModifier(modifier: DrawModifier | undefined): T
```

Sets the drawModifier of the current component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [DrawModifier](arkts-arkui-common-comp-drawmodifier-c.md) &#124; undefined | Yes | drawModifier used to draw, or undefined if it is not available. Default value: undefined A custom modifier applies only to the FrameNode of the currently bound component, not to its subnodes. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## enableClickSoundEffect

```TypeScript
enableClickSoundEffect(enabled: boolean | undefined): T
```

Sets whether to enable the default click sound effect for a component. Whether the sound can be played depends on the sound settings of the device. For example, the sound effect is not played in mute mode.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Whether to enable the default click sound effect for a component.<br>The value **true** indicates that the default click sound effect is enabled, and **false** indicates the opposite. <br>If the value is **undefined**, the default click sound effect is enabled. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## enabled

```TypeScript
enabled(value: boolean): T
```

If the value is true, the component is available and can respond to operations such as clicking. If it is set to false, click operations are not responded.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## expandSafeArea

```TypeScript
expandSafeArea(types?: Array<SafeAreaType>, edges?: Array<SafeAreaEdge>): T
```

Controls a component to expand its safe area to achieve an immersive effect.

> **NOTE:** 
> 
> - When using **expandSafeArea** to expand the drawing of a component, avoid setting fixed width and height values (except percentages). If fixed width and height values or 'auto' are set, the safe area can be expanded only upward (SafeAreaEdge.TOP) and toward the start direction (SafeAreaEdge.START, which indicates the left side in LTR mode and the right side in RTL mode), and the size of the expanded component remains unchanged.
> 
> - The safe area does not restrict the layout and size of internal components, nor does it clip internal components.
> 
> - When the parent container is a scrollable container, after the **expandSafeArea** attribute is set on a component, the component itself does not extend, but it can still trigger the update of the extension range of its child nodes on which **expandSafeArea** is set.
> 
> - When **expandSafeArea()** is set without parameters, the default values are used. When
> **expandSafeArea([],[])** is set, the input parameters are empty arrays, and the **expandSafeArea** attribute
> does not take effect.
> 
> - The conditions for the **expandSafeArea** attribute to take effect on a component are as follows:
> 1. When type is SafeAreaType.KEYBOARD, it takes effect by default, meaning that the component does not avoid the keyboard.<br>
> 2. When other types are set, the component can extend under the safe area only when the component boundary coincides with the safe area. For example, if the height of the status bar at the top of the device is 100, the absolute position of the component on the screen must satisfy 0 &lt;= y &lt;= 100.
> 
> - When a component extends into a non-safe area, events in the non-safe area, such as click events, may be intercepted by the system and preferentially responded to by system components such as the status bar. &gt;

> - It is not recommended to set the **expandSafeArea** attribute on components in a scrollable container. If it is set, the **expandSafeArea** attribute must be set on all direct nodes from the current node to the scrollable ancestor container according to the component nesting relationship. Otherwise, the **expandSafeArea** attribute may become invalid after scrolling.
> 
> - The **expandSafeArea** attribute takes effect only on the current component and is not passed to parent or child components. Therefore, developers must configure this attribute separately for all related components.
> 
> - When both **expandSafeArea** and **position** are set, the **position** attribute takes effect first, and the
> **expandSafeArea** attribute takes effect later. For components on which drawing attributes such as position and
> offset are not set, if their boundaries do not overlap with the non-safe area, setting the **expandSafeArea**
> attribute does not take effect, such as dialog boxes and semi-modal components.
> 
> - For scenarios where the **expandSafeArea** attribute cannot take effect, to place a component in the non-safe area, you need to manually adjust the coordinates of the component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[SafeAreaType](arkts-arkui-common-comp-safeareatype-e.md)&gt; | No | Types of the safe areas to expand. By default, SafeAreaType.CUTOUT is included. However, if the Metadata configuration item is not added, the page does not avoid the cutout, and the CUTOUT type does not take effect.<br>Default value: [SafeAreaType.SYSTEM, SafeAreaType.CUTOUT, SafeAreaType.KEYBOARD]<br>Invalid value: handled by default. |
| edges | Array&lt;[SafeAreaEdge](arkts-arkui-common-comp-safeareaedge-e.md)&gt; | No | Edges of the safe areas to expand. By default, the component expands to all avoidance areas.<br>Default value: [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM, SafeAreaEdge.START, SafeAreaEdge.END].<br>Invalid value: handled by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## flexBasis

```TypeScript
flexBasis(value: number | string): T
```

Sets the base size of a component. This attribute can be set only when the component is a child of a Flex, Column, Row, or DynamicLayout container. After it is set, the component uses this base size as its initial size in layout calculation. When the parent container is Column or Row, you must set the size along the main axis. When the main axis size (width/height/size) is not set, Column and Row still follow the default layout behavior and adapt to the child component size on the main axis, which may affect the effect of flexBasis.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Base size of the component on the main axis of the parent container. <br>Default value: 'auto' (indicating that the base size of the component on the main axis is the original size of the component). <br>string type: percentage strings are not allowed. Optional values: a string that can be converted to a number (for example, '10'), a string with a length unit (for example, '10px'), or 'auto'. If a string that does not meet the requirements is passed in, the default value 'auto' is used. <br>number: value range (0, +∞), in vp (virtual pixel). <br>When an invalid value is set, this attribute is processed as the default value 'auto'. <br>[constraintSize](#constraintsize) restricts the size range of the component. When the base size set by flexBasis exceeds the restriction range of constraintSize, it is constrained by constraintSize. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## flexGrow

```TypeScript
flexGrow(value: number): T
```

Sets the proportion of the component in the remaining space of the parent container. This attribute can be set only when the component is a child of a Flex, Column, Row, or DynamicLayout container. After it is set, the component expands according to the ratio to occupy the remaining space of the parent container. When the parent container is Column or Row, you must set the size along the main axis. When the main axis size (width/height/size) is not set, Column and Row still follow the default layout behavior and adapt to the child component size on the main axis, which may affect the remaining space allocation effect of flexGrow. Setting this attribute triggers a second layout. In scenarios with strict performance requirements, use **layoutWeight** instead.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Sets the proportion of the remaining space in the parent container along the main axis (horizontal for row layout and vertical for column layout) allocated to the component where this attribute resides. The value 0 means the component does not participate in the allocation of remaining space and keeps its original size. When the value is greater than 0, the remaining space of the parent container is allocated proportionally; the larger the value, the more space is allocated.<br>Value range: 0, +∞)<br>Default value: 0<br>When the parent container is [Column or Row, you need to set the size along the main axis (width/height/size); otherwise, the remaining space allocation effect of flexGrow may be affected.<br>[constraintSize](#constraintsize) restricts the size range of the component. When the component size after flexGrow expansion exceeds the maximum limit of constraintSize, it is constrained by constraintSize.<br>When an invalid value is set, this attribute takes the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## flexShrink

```TypeScript
flexShrink(value: number): T
```

Sets the proportion of the shrink size allocated to the component where this attribute resides when the parent container runs out of space. This attribute can be set only when the component is a child of a Flex, Column, Row, or DynamicLayout container. When the parent container is Column or Row, the parent container must set the size along the main axis (that is, width/height/size) for flexShrink to take effect. When the main axis size (width/height/size) is not set, Column and Row still follow the default layout behavior and adapt to the child component size on the main axis, in which case flexShrink does not take effect. Setting this attribute triggers a second layout. In scenarios with strict performance requirements, use **layoutWeight** instead.

When [getInspectorByKey](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#getinspectorbykey9) is used to obtain the **flexShrink** attribute, if the node does not have **flexShrink** set, the default value of **1** is returned by default (consistent with the default value of the Flex container, but different from the default value **0** of the Column and Row containers).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Sets the proportion of the compressed size allocated to the component to which this attribute belongs when the parent container space is insufficient. The value 0 indicates that the component does not participate in compression; when the value is greater than 0, compression is performed proportionally, and a larger value indicates a larger compression amount.<br>When the parent container is Column or Row, default value: 0, value range: 0, +∞).<br>When the parent container is [Flex, default value: 1, value range: [0, +∞).<br>[constraintSize](#constraintsize) restricts the size range of the component. Even if [constraintSize](#constraintsize) is set for Column and Row, when the main axis size (width/height/size) is not set in the parent container, the default layout behavior is still followed, and the component size is adapted to the children on the main axis. In this case, flexShrink does not take effect.<br>When an exception value is set, this attribute uses the default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## focusable

```TypeScript
focusable(value: boolean): T
```

Sets whether the component is focusable.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the component is focusable.<br>**true**: The component is focusable.<br> **false**: The component is not focusable.<br>**NOTE:** <br>Components that have default interaction logic, such as [Button](arkts-arkui-common-comp-mouseevent-i.md#button) and TextInput, are focusable by default. Other components, such as Text and Image, are not focusable by default. Only focusable components can trigger a focus event. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## focusBox

```TypeScript
focusBox(style: FocusBoxStyle): T
```

Sets the system focus box style for the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [FocusBoxStyle](../arkts-apis/arkts-arkui-focusboxstyle-i.md) | Yes | System focus box style for the component.<br>**NOTE:** <br>This style affects only the components that display the system focus box during focus traversal. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## focusOnTouch

```TypeScript
focusOnTouch(value: boolean): T
```

Sets whether the component is focusable on touch. If **focusOnTouch** is not set, the component is not focusable on touch by default.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the component is focusable on touch.<br>**true**: The component is focusable on touch.<br>**false**: The component is not focusable on touch.<br>**NOTE:** <br>This setting requires the component to be touchable. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## focusScopeId

```TypeScript
focusScopeId(id: string, isGroup?: boolean): T
```

Set container as a focus group with a specific identifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | focus scope identifier. |
| isGroup | boolean | No | whether this scope is a focus group, the default value is false |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="focusscopeid-1"></a>

## focusScopeId

```TypeScript
focusScopeId(id: string, isGroup?: boolean, arrowStepOut?: boolean): T
```

Set container as a focus group with a specific identifier.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | focus scope identifier. |
| isGroup | boolean | No | whether this scope is a focus group, the default value is false. |
| arrowStepOut | boolean | No | whether the arrow keys can move focus from inside the focus group to outside, only effective when isGroup is true, the default value is true. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## focusScopePriority

```TypeScript
focusScopePriority(scopeId: string, priority?: FocusPriority): T
```

Set the focus priority of component in a specific focus scope.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scopeId | string | Yes |  |
| priority | [FocusPriority](../arkts-apis/arkts-arkui-focuspriority-e.md) | No | the default value is AUTO |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## foregroundBlurStyle

```TypeScript
foregroundBlurStyle(value: BlurStyle, options?: ForegroundBlurStyleOptions): T
```

Applies a foreground blur style to the component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 18.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md) | Yes | Settings of the foreground blur style. |
| options | [ForegroundBlurStyleOptions](arkts-arkui-common-comp-foregroundblurstyleoptions-i.md) | No | Defines the foreground blur options. For details about the default value, see [ForegroundBlurStyleOptions](arkts-arkui-common-comp-foregroundblurstyleoptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="foregroundblurstyle-1"></a>

## foregroundBlurStyle

```TypeScript
foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions): T
```

Applies a foreground blur style to the component. Compared to [foregroundBlurStyle](#foregroundblurstyle), the **style** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes | Settings of the foreground blur style.<br>If **style** is set to **undefined**, no blur is applied. |
| options | [ForegroundBlurStyleOptions](arkts-arkui-common-comp-foregroundblurstyleoptions-i.md) | No | Defines the foreground blur options. For details about the default value, see [ForegroundBlurStyleOptions](arkts-arkui-common-comp-foregroundblurstyleoptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="foregroundblurstyle-2"></a>

## foregroundBlurStyle

```TypeScript
foregroundBlurStyle(style: Optional<BlurStyle>, options?: ForegroundBlurStyleOptions, sysOptions?: SystemAdaptiveOptions): T
```

Foreground blur style. blurStyle:Blur style type. sysOptions: system adaptive options.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes |  |
| options | [ForegroundBlurStyleOptions](arkts-arkui-common-comp-foregroundblurstyleoptions-i.md) | No |  |
| sysOptions | [SystemAdaptiveOptions](arkts-arkui-common-comp-systemadaptiveoptions-i.md) | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## foregroundColor

```TypeScript
foregroundColor(value: ResourceColor | ColoringStrategy): T
```

Sets the foreground color of the component. Components without explicit foreground color settings inherit from their parent components by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [ColoringStrategy](../arkts-apis/arkts-arkui-coloringstrategy-e.md) | Yes | Foreground color. The value can be a specific color or a coloring strategy. The attribute animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="foregroundcolor-1"></a>

## foregroundColor

```TypeScript
foregroundColor(color: Optional<ResourceColor | ColoringStrategy>): T
```

Sets the foreground color of the component. Components without explicit foreground color settings inherit from their parent components by default. Compared to [foregroundColor](#foregroundcolor), the **color** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [ColoringStrategy](../arkts-apis/arkts-arkui-coloringstrategy-e.md)&gt; | Yes | Foreground color. The value can be a specific color or a coloring strategy. Property animations are not supported.<br>If the color value is **undefined**, the previous setting or the component's default value is retained. The specific behavior may vary across components. It is recommended that you use explicit color values or [ColoringStrategy](../arkts-apis/arkts-arkui-coloringstrategy-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## foregroundEffect

```TypeScript
foregroundEffect(options: ForegroundEffectOptions): T
```

Sets the foreground effect of the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ForegroundEffectOptions](arkts-arkui-common-comp-foregroundeffectoptions-i.md) | Yes | Foreground effect settings, including the blur radius. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## foregroundFilter

```TypeScript
foregroundFilter(filter: Filter): T
```

Sets the visual effect of the foreground (content) filter.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [Filter](arkts-arkui-common-comp-filter-t.md) | Yes | Visual effect of the foreground (content) filter. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## freeze

```TypeScript
freeze(value: boolean): T
```

Sets whether to freeze the component. When frozen, the component and its children are cached for repeated drawing after offscreen rendering, without updating internal attributes.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to freeze the component. When frozen, the component and its children are cached for repeated drawing after offscreen rendering, without updating internal attributes. If the opacity of the component is not 1, the drawing effect may vary depending on the value.<br>Default value: **false**<br> **true**: Freeze the component.<br>**false**: Do not freeze the component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="freeze-1"></a>

## freeze

```TypeScript
freeze(freeze: Optional<boolean>): T
```

Sets whether to freeze the component. When frozen, the component and its children are cached for repeated drawing after offscreen rendering, without updating internal attributes. Compared with [freeze](#freeze), this API supports the **undefined** type for the **freeze** parameter.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| freeze | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to freeze the component. When frozen, the component and its children are cached for repeated drawing after offscreen rendering, without updating internal attributes. If the opacity of the component is not 1, the drawing effect may vary depending on the value.<br>Default value: **false**<br> **true**: Freeze the component.<br>**false**: Do not freeze the component.<br>If **freeze** is set to **undefined**, the previous value is retained. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## geometryTransition

```TypeScript
geometryTransition(id: string): T
```

Implements an implicit shared element transition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID used to set up a binding relationship. Setting **id** to an empty string clears the binding relationship. The value can be changed to re-establish the binding relationship. One ID can be bound to only two components, which function as in and out components. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="geometrytransition-1"></a>

## geometryTransition

```TypeScript
geometryTransition(id: string, options?: GeometryTransitionOptions): T
```

Implements an implicit shared element transition.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID used to set up a binding relationship. Setting **id** to an empty string clears the binding relationship. The value can be changed to re-establish the binding relationship. One ID can be bound to only two components, which function as in and out components. |
| options | [GeometryTransitionOptions](arkts-arkui-common-comp-geometrytransitionoptions-i.md) | No | Settings of the implicit shared element transition. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## gesture

```TypeScript
gesture(gesture: GestureType, mask?: GestureMask): T
```

Gesture to bind.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | GestureType | Yes | Type of the gesture to bind. |
| mask | [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | No | Mask for gesture events.<br>Default value: **GestureMask.Normal**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## gestureModifier

```TypeScript
gestureModifier(modifier: GestureModifier): T
```

Creates a gesture modifier.

> **NOTE:** 
> 
> **gestureModifier** does not support custom components.
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [GestureModifier](arkts-arkui-common-comp-gesturemodifier-i.md) | Yes | for dynamically setting gestures bound to the current component. The if/else syntax is supported. modifier: gesture modifier. You need a custom class to implement the GestureModifier API. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## grayscale

```TypeScript
grayscale(value: number): T
```

Applies a grayscale effect to the component. The grayscale rendering of the upper layer will overlay that of lower- layer child components. If this API is not used, there will be no change by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Grayscale conversion ratio of the component. If the value is **1.0**, the component is completely converted to grayscale. If the value is **0.0**, the component remains unchanged. Between **0** and **1**, the value applies a linear multiplier on the grayscale effect.<br>Value range: [0.0, 1.0]<br>**NOTE:** <br>A value less than **0.0** evaluates to the value **0.0**. A value greater than **1.0** evaluates to the value **1.0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="grayscale-1"></a>

## grayscale

```TypeScript
grayscale(grayscale: Optional<number>): T
```

Applies a grayscale effect to the component. The grayscale rendering of the upper layer will overlay that of lower- layer child components. If this API is not used, there will be no change by default. Compared to [grayscale](#grayscale), the **grayscale** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| grayscale | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Grayscale conversion ratio of the component. If the value is **1.0**, the component is completely converted to grayscale. If the value is **0.0**, the component remains unchanged. Between **0** and **1**, the value applies a linear multiplier on the grayscale effect.<br>Value range: [0.0, 1.0]<br>**NOTE:** <br>A value less than **0.0** evaluates to the value **0.0**. A value greater than **1.0** evaluates to the value **1.0**.<br>If **grayscale** is set to **undefined**, the default value **0.0** is used, which means the component reverts to its original effect with no grayscale. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## gridOffset

```TypeScript
gridOffset(value: number): T
```

Default offset column count, which refers to the number of columns by which the current component is offset along the Start direction of its parent component when the useSizeType attribute does not set the offset for the corresponding size. That is, the starting position of the component is offset by n columns relative to the Start direction of the parent component. It must be a non-negative integer. When passing a negative number, use the default value 0. When useSizeType sets the offset for the corresponding size, the gridOffset setting does not take effect.

> **NOTE:** 
> 
> - When calling this attribute, its parent component or ancestor component must be GridContainer.
> - After this attribute is configured, the layout of the current component in the horizontal direction of the parent component no longer follows the original layout mode of the parent component. Instead, the component is offset by a certain distance along the Start direction of the parent component.
> - Offset distance = (column width + spacing)* offset column count.
> - Sibling components after the component with the offset (gridOffset) set are laid out relative to this component.

**Since:** 7

**Deprecated since:** 14

**Substitutes:** grid_col/GridColInterface and grid_row/GridRowInterface

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Default offset column count. Default value: **0** |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## gridSpan

```TypeScript
gridSpan(value: number): T
```

Default column count, which refers to the grid column count occupied when the useSizeType attribute does not set the column count (span) for the corresponding size. It must be a non-negative integer. When passing a negative number or a value exceeding the total column count of GridContainer, use the default value 1.

> **NOTE:** 
> 
> - When calling this attribute, its parent component or ancestor component must be GridContainer.
> - When the grid span attribute is set, the width of the component is determined by the grid layout.

**Since:** 7

**Deprecated since:** 14

**Substitutes:** grid_col/GridColInterface and grid_row/GridRowInterface

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Default column count. Default value: **1** |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## groupDefaultFocus

```TypeScript
groupDefaultFocus(value: boolean): T
```

Specifies whether to set the component as the default focus of the container. If **groupDefaultFocus** is not set, the component will not receive focus by default when its container is focused.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to set the component as the default focus of the parent container. This parameter takes effect only when the container is new and obtains focus for the first time. <br>**true**: The component is the default focus of the parent container.<br>**false**: The component is not the default focus of the parent container.<br>**NOTE:** <br>This parameter must be used together with [tabIndex](#tabindex). When **tabIndex** is set for a container and **groupDefaultFocus(true)** is set for a child in the container or for the container itself, then when the container obtains focus for the first time through sequential Tab navigation, the focus automatically moves to the specified component. If **groupDefaultFocus(true)** is set for multiple components in the container (including the container itself), the first component found in the component tree in-depth traversal receives the focus. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## height

```TypeScript
height(value: Length): T
```

Sets the height of the component itself. By default, the height required for the content of the child component is used. If the height of a child component is greater than that of its parent component, the child component overflows and is displayed outside the parent component. <br>Since API version 10, this API supports the calc calculation feature.

> **NOTE:** 
> 
> In the Row, Column, and RelativeContainer
> components, setting **width** and **height** to **auto** means that the size adapts to the size of their
> child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Component height to set.<br>Unit: vp<br>When a percentage is set, the height of the parent container is used as the base value.<br>Abnormal values: If the parameter is **undefined**, the attribute setting does not take effect; for other abnormal values, the height attribute is restored to the default behavior when it is not configured. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="height-1"></a>

## height

```TypeScript
height(heightValue: Length | LayoutPolicy): T
```

Sets the height of the component itself or its vertical layout policy. By default, the height required for the content of the child component is used. If the height of a child component is greater than that of its parent component, the child component overflows and is displayed outside the parent component. <br>Since API version 15, when the parameter is of the Length type, this API supports the calc calculation feature.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| heightValue | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [LayoutPolicy](arkts-arkui-common-comp-layoutpolicy-c.md) | Yes | Component height or vertical layout policy to set.<br>Unit: vp<br>When a percentage is set, the height of the parent container is used as the base value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## hitTestBehavior

```TypeScript
hitTestBehavior(value: HitTestMode): T
```

Sets the hit test mode for a component. If **hitTestBehavior** is not set, the component defaults to **HitTestMode.Default**.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [HitTestMode](../arkts-apis/arkts-arkui-hittestmode-e.md) | Yes | Hit test mode for a component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## hoverEffect

```TypeScript
hoverEffect(value: HoverEffect): T
```

Sets the hover effect for the component. When no hover effect is specified, the component uses the default **HoverEffect.Auto** effect. For components with hover effects applied, the hover effect is hidden when the mouse hovers and presses down on the component, and restored when the mouse button is released.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [HoverEffect](../arkts-apis/arkts-arkui-hovereffect-e.md) | Yes | Hover effect of the component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## hueRotate

```TypeScript
hueRotate(value: number | string): T
```

Rotates the hue of the component. If this API is not used, there will be no change by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Hue rotation angle of the component.<br>Value range: (-∞, +∞)<br>**NOTE:** <br>A rotation of 360 degrees leaves the color unchanged. A rotation of 180 degrees and then -180 degrees also leaves the color unchanged. When the data type is number, the value **90** is equivalent to **'90deg'**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="huerotate-1"></a>

## hueRotate

```TypeScript
hueRotate(rotation: Optional<number | string>): T
```

Rotates the hue of the component. If this API is not used, there will be no change by default. Compared to [hueRotate](#huerotate), the **rotation** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotation | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; string&gt; | Yes | Hue rotation angle of the component.<br>Value range: (-∞, +∞)<br> For the string type, the value must be a numeric string.<br>**NOTE:** <br>A rotation of 360 degrees leaves the color unchanged. A rotation of 180 degrees and then -180 degrees also leaves the color unchanged. When the data type is number, the value **90** is equivalent to **'90deg'**.<br>If **sepia** is **undefined**, the component reverts to its original effect with no hue rotation. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## id

```TypeScript
id(value: string): T
```

Id. User can set an id to the component to identify it.

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): T
```

Safe area when expanding the component layout. The component layout position and size may change, which differs from the expandSafeArea mechanism (which only expands the drawing area and keeps the layout unchanged).

> **NOTE:** 
> 
> - For a component that ignores layout safe area edges: If its width or height is set to [LayoutPolicy.matchParent](arkts-arkui-common-comp-layoutpolicy-c.md#matchparent), both its size and position will change; otherwise, only its position will change.
> 
> - Based on the **safeAreaPadding** accumulation feature, a component can expand its safe area edges to all detectable continuous safe areas.
> 
> - When child elements of scrollable components ignore layout safe area edges, the safe areas of the scrollable component itself and its parent components are not considered in the scrolling direction. Scrollable components include **List**, **ArcListItem**, **Grid**, **WaterFlow**, **Swiper**, and **Tabs**.
> 
> - When both the layout safe area ignore attribute (**.ignoreLayoutSafeArea**) and the rendering safe area ignore attribute (**.expandSafeArea**) are set: **.ignoreLayoutSafeArea** takes effect first, and **.expandSafeArea**takes effect on the basis of the former.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | Array&lt;[LayoutSafeAreaType](arkts-arkui-common-comp-layoutsafeareatype-e.md)&gt; | No | Type of the expanded layout safe area.<br>Default value: [LayoutSafeAreaType.SYSTEM], which extends to the system safe area, for example, the status bar, navigation bar, punch-hole area, and component-level safe area ([safeAreaPadding](#safeareapadding)). <br>Invalid value: handled by default. |
| edges | Array&lt;[LayoutSafeAreaEdge](arkts-arkui-common-comp-layoutsafeareaedge-e.md)&gt; | No | Edges of the expanded layout safe area, with mirroring supported.<br>Default value: [LayoutSafeAreaEdge.ALL], which expands all edges of the component.<br>Invalid value: handled by default. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## inspectorLabel

```TypeScript
inspectorLabel(label: string | undefined): T
```

Set the component's inspector label which only display on DevEco Studio.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| label | string &#124; undefined | Yes | the inspector label. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## invert

```TypeScript
invert(value: number | InvertOptions): T
```

Inverts an image.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [InvertOptions](arkts-arkui-common-comp-invertoptions-i.md) | Yes | How an image is inverted.<br>When the input parameter is a number: If the value is **1**, the component is completely inverted. If the value is **0**, the component remains unchanged.<br>Value range: [0, 1].<br>A value less than 0 evaluates to the value **0**. A value larger than 1 is treated as **1**.<br>If the value is of the InvertOptions type, the grayscale value of the background color is compared with the threshold range. If the grayscale value is greater than the upper bound of the threshold range, the **high** value is used. If the grayscale value is less than the lower bound of the threshold range, the **low** value is used. If the grayscale value is within the threshold range, the background color changes linearly from high to low.<br>**NOTE:** <br>The number and InvertOptions parameter types produce different inversion effects. When you switch parameter types, previous effects persist and both effects coexist. Use consistent parameter types for predictable results.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="invert-1"></a>

## invert

```TypeScript
invert(options: Optional<number | InvertOptions>): T
```

Inverts an image. Compared with [invert](#invert), this API supports the **undefined** type for the **options** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [InvertOptions](arkts-arkui-common-comp-invertoptions-i.md)&gt; | Yes | How an image is inverted.<br>When the input parameter is a number: If the value is **1**, the component is completely inverted. If the value is **0**, the component remains unchanged.<br>Value range: [0, 1].<br>A value less than 0 evaluates to the value **0**. A value larger than 1 is treated as **1**.<br>If the value is of the InvertOptions type, the grayscale value of the background color is compared with the threshold range. If the grayscale value is greater than the upper bound of the threshold range, the **high** value is used. If the grayscale value is less than the lower bound of the threshold range, the **low** value is used. If the grayscale value is within the threshold range, the background color changes linearly from high to low.<br>If **options** is **undefined**, the component reverts to its original effect.<br>**NOTE:** <br>The number and InvertOptions parameter types produce different inversion effects. When you switch parameter types, previous effects persist and both effects coexist. Use consistent parameter types for predictable results. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## key

```TypeScript
key(value: string): T
```

Key. User can set an key to the component to identify it.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## keyboardShortcut

```TypeScript
keyboardShortcut(value: string | FunctionKey, keys: Array<ModifierKey>, action?: () => void): T
```

Sets a keyboard shortcut for the component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [FunctionKey](../arkts-apis/arkts-arkui-functionkey-e.md) | Yes | Character key (which can be entered through the keyboard) or function key.<br>An empty string means to disable the keyboard shortcut.<br> |
| keys | Array&lt;[ModifierKey](../arkts-apis/arkts-arkui-modifierkey-e.md)&gt; | Yes | Modifier keys.<br>This parameter can be left empty only when **value** is set to a function key.<br> |
| action | () =&gt; void | No | Callback for a custom event after the keyboard shortcut is triggered. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## layoutGravity

```TypeScript
layoutGravity(alignment: LocalizedAlignment): T
```

Sets the alignment rule for child components in the **Stack** container. This API only takes effect when the parent container is **Stack**. When used with the align attribute, **layoutGravity** takes precedence. This attribute supports dynamic configuration via [attributeModifier](#attributemodifier).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignment | [LocalizedAlignment](../arkts-apis/arkts-arkui-localizedalignment-e.md) | Yes | Alignment rule of child components in the **Stack** container. If an invalid value is passed, the default value is used. Default value: **LocalizedAlignment.CENTER**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## layoutWeight

```TypeScript
layoutWeight(value: number | string): T
```

Sets the layout weight of a component so that the component is allocated a size in the main-axis direction of the parent container ([Row](arkts-arkui-row-comp.md#row)/[Column](arkts-arkui-column-comp.md#column)/[Flex](arkts-arkui-flex-comp.md#flex)) according to the weight. It applies to scenarios where the parent container size is determined and multiple child components need to allocate the remaining space proportionally.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | When the size of the parent container is determined, child components that do not have the **layoutWeight** attribute set or whose effective **layoutWeight** value is **0** take priority in occupying space. The space left on the main axis after these child components occupy space is called the remaining space on the main axis. Child components that have the **layoutWeight** attribute set and whose effective **layoutWeight** value is greater than 0 are allocated sizes from the remaining space on the main axis according to their respective weight proportions. During allocation, the **width**\/**height** settings of the child components are ignored, but the **minWidth**\/ **minHeight** constraints are retained.<br>Default value: 0<br>Value range: [0, +∞)<br>When the value is out of range: if a value less than 0 is passed in, it is processed as 0.<br>**NOTE:** <br>This attribute takes effect only in the [Row](arkts-arkui-row-comp.md#row)/[Column](arkts-arkui-column-comp.md#column)/[Flex](arkts-arkui-flex-comp.md#flex) layout.<br>The optional value is a number greater than or equal to 0, or a string that can be converted to a number (integer and decimal formats are supported).<br>If a child component in the container has the **layoutWeight** attribute set and the set value is greater than 0, all child components are no longer laid out based on [flexShrink](#flexshrink) and [flexGrow](#flexgrow). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## lightUpEffect

```TypeScript
lightUpEffect(value: number): T
```

Applies a light up effect to the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Light up degree of the component.<br>The value ranges from 0 to 1.<br>If the value is **0**, the component is dark. If the value is **1**, the component is fully illuminated. Between **0** and **1**, a larger value indicates higher luminance. A value less than 0 is handled as the value **0**. A value greater than 1 is handled as the value **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="lightupeffect-1"></a>

## lightUpEffect

```TypeScript
lightUpEffect(degree: Optional<number>): T
```

Applies a light up effect to the component. Compared to [lightUpEffect&lt;sup&gt;12+&lt;/sup&gt;](#lightupeffect), the **degree** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Light up degree of the component.<br>The value ranges from 0 to 1.<br>If the value is **0**, the component is dark. If the value is **1**, the component is fully illuminated. Between **0** and **1**, a larger value indicates higher luminance. A value less than 0 is handled as the value **0**. A value greater than 1 is handled as the value **1**.<br>If **degree** is **undefined**, the light up degree reverts to **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## linearGradient

```TypeScript
linearGradient(value: LinearGradientOptions): T
```

Creates a linear gradient.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LinearGradientOptions](arkts-arkui-common-comp-lineargradientoptions-i.md) | Yes | Linear gradient.<br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="lineargradient-1"></a>

## linearGradient

```TypeScript
linearGradient(options: Optional<LinearGradientOptions>): T
```

Creates a linear gradient. Compared to [linearGradient](#lineargradient), this API supports the **undefined** type for the **options** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[LinearGradientOptions](arkts-arkui-common-comp-lineargradientoptions-i.md)&gt; | Yes | Linear gradient.<br>If **options** is **undefined**, the linear gradient is disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## linearGradientBlur

```TypeScript
linearGradientBlur(value: number, options: LinearGradientBlurOptions): T
```

Applies a linear gradient foreground blur effect to the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Blur radius. A larger value indicates a higher blur degree. If the value is 0, the content is not blurred.<br>Value range: [0, 1000] |
| options | [LinearGradientBlurOptions](arkts-arkui-common-comp-lineargradientbluroptions-i.md) | Yes | Linear gradient blur effect.<br>The linear gradient blur effect is defined by [fractionStops](arkts-arkui-common-comp-lineargradientbluroptions-i.md) and [direction](arkts-arkui-common-comp-lineargradientbluroptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="lineargradientblur-1"></a>

## linearGradientBlur

```TypeScript
linearGradientBlur(blurRadius: Optional<number>, options: Optional<LinearGradientBlurOptions>): T
```

Applies a linear gradient foreground blur effect to the component. Compared with [linearGradientBlur&lt;sup&gt;12+&lt;/sup&gt;](#lineargradientblur), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Blur radius. A larger value indicates a higher blur degree. If the value is 0, the content is not blurred.<br>Value range: [0, 1000]<br>If **blurRadius** is **undefined**, the gradient blur effect reverts to **0**. |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[LinearGradientBlurOptions](arkts-arkui-common-comp-lineargradientbluroptions-i.md)&gt; | Yes | Linear gradient blur effect.<br>If **options** is **undefined**, the gradient blur effect reverts to **0**.<br>The linear gradient blur effect is defined by [fractionStops](arkts-arkui-common-comp-lineargradientbluroptions-i.md) and [direction](arkts-arkui-common-comp-lineargradientbluroptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## margin

```TypeScript
margin(value: Margin | Length | LocalizedMargin): T
```

Sets the margin of the component. The margin is considered as a part of the component's size during position calculation, thereby affecting the component's placement. <br>Since API version 10, this API supports the calc calculation feature.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Margin](../arkts-apis/arkts-arkui-margin-t.md) &#124; [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [LocalizedMargin](../arkts-apis/arkts-arkui-localizedmargin-t.md) | Yes | Margin of the component.<br>When the parameter is of the **Length** type, the margins in all four directions take effect at the same time.<br>Default value: **0**<br>Unit: vp<br>When **margin** is set as a percentage, the top, bottom, left, and right margins all use the width of the parent container as the base value. When laying out in the cross-axis direction of [Row](arkts-arkui-row-comp.md#row), [Column](arkts-arkui-column-comp.md#column), and [Flex](arkts-arkui-flex-comp.md#flex), the space occupied by a child component in the cross-axis direction includes the size of the child component itself and the **margin** value.<br>For example, if a **Column** container has a width of 100, a child component has a width of 50, and the left and right margins are 10 and 20 respectively, the sum of the child component width and the left and right margins is 50 + 10 + 20 = 80, which is less than the container width of 100. The child component is center-aligned in the cross-axis direction, leaving (100 - 80)/2 = 10 of blank space on each of the left and right sides in the horizontal direction.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## markAnchor

```TypeScript
markAnchor(value: Position | LocalizedPosition): T
```

Sets the anchor for element positioning. This attribute supports dynamic configuration via [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position &#124; [LocalizedPosition](../arkts-apis/arkts-arkui-localizedposition-i.md) | Yes | Positioning anchor that offsets an element from the position specified by position or offset **.position({x: value1, y: value2}).markAnchor({x: value3, y: value4})** has the same effect as **.position({x: value1 - value3, y: value2 - value4})**. The same applies to **offset**.<br>If **.markAnchor({x: value1, y: value2})** is set separately, the effect is the same as that of **.offset({x: -value1, y: -value2})**. <br>API version 9 and earlier: The default value is **{x: 0, y: 0}**. <br>API version 10: no default value. <br>This attribute does not take effect when it is set to an abnormal value.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## mask

```TypeScript
mask(value: ProgressMask): T
```

Adds a mask to the component to indicate the progress.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ProgressMask](arkts-arkui-common-comp-progressmask-c.md) | Yes | Mask to add to the component, which allows for dynamic adjustment of progress, maximum value, and color settings. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="mask-1"></a>

## mask

```TypeScript
mask(mask: Optional<ProgressMask>): T
```

Adds a mask to the component to indicate the progress. Compared with [mask&lt;sup&gt;12+&lt;/sup&gt;](#mask), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mask | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ProgressMask](arkts-arkui-common-comp-progressmask-c.md)&gt; | Yes | Mask to add to the component, which allows for dynamic adjustment of progress, maximum value, and color settings.<br>If **mask** is set to **undefined**, the component to revert to its original effect without the mask to indicate the progress. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="mask-2"></a>

## mask

```TypeScript
mask(value: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute | ProgressMask): T
```

Adds a mask of the specified shape to the component.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** [maskShape](#maskshape)

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CircleAttribute](arkts-arkui-circle-comp-attribute.md) &#124; [EllipseAttribute](arkts-arkui-ellipse-comp-attribute.md) &#124; [PathAttribute](arkts-arkui-path-comp-attribute.md) &#124; [RectAttribute](arkts-arkui-rect-comp-attribute.md) &#124; [ProgressMask](arkts-arkui-common-comp-progressmask-c.md) | Yes | Mask of the specified shape to add to the component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## maskShape

```TypeScript
maskShape(value: CircleShape | EllipseShape | PathShape | RectShape): T
```

Adds a mask of the specified shape to the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CircleShape](arkts-arkui-common-comp-circleshape-t.md) &#124; [EllipseShape](arkts-arkui-common-comp-ellipseshape-t.md) &#124; [PathShape](arkts-arkui-common-comp-pathshape-t.md) &#124; [RectShape](arkts-arkui-common-comp-rectshape-t.md) | Yes | Mask of the specified shape to add to the component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="maskshape-1"></a>

## maskShape

```TypeScript
maskShape(shape: Optional<CircleShape | EllipseShape | PathShape | RectShape>): T
```

Adds a mask of the specified shape to the component. Compared with [maskShape&lt;sup&gt;12+&lt;/sup&gt;](#maskshape), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CircleShape](arkts-arkui-common-comp-circleshape-t.md) &#124; [EllipseShape](arkts-arkui-common-comp-ellipseshape-t.md) &#124; [PathShape](arkts-arkui-common-comp-pathshape-t.md) &#124; [RectShape](arkts-arkui-common-comp-rectshape-t.md)&gt; | Yes | Mask of the specified shape to add to the component.<br>If the value of **shape** is **undefined**, the current setting will be reset to its default state. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## materialFilter

```TypeScript
materialFilter(filter: Filter | undefined): T
```

Sets the visual effect of the material filter. The effects it contains are rendered at a level before the shadow.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [Filter](arkts-arkui-common-comp-filter-t.md) &#124; undefined | Yes | Filter effect parameters. Undefined means to none material filter. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## monopolizeEvents

```TypeScript
monopolizeEvents(monopolize: boolean): T
```

Sets whether the component exclusively handles events.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| monopolize | boolean | Yes | Whether the component exclusively handles events. true: The component exclusively handles events. false: The component does not exclusively handle events. Default value: false. NOTE 1. If a component is exclusively handling events after a finger is pressed on it, and another finger is pressed before the first finger is lifted, the component continues to exclusively handle events while interacting with the second finger. The same case applies to a third and more fingers. 2. If a component is bound through [parallelGesture](#parallelgesture) to a gesture, for example, pan gesture, that can also be triggered by its child component, and the child component has event monopolization and is the first to respond, then the parent will not respond to the gesture. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## motionBlur

```TypeScript
motionBlur(value: MotionBlurOptions):T
```

Applies a motion blur effect to the component being scaled or moved.

> **NOTE:** 
> 
> - Do not use this API in intra-component transitions, shared element transitions, implicit element transitions,or particle animations. Doing so may cause unexpected results.
> 
> - The **radius** parameter of **motionBlur** must be set to **0** for the initial state. Otherwise, there may be unexpected results during a cold start.
> 
> - This API must be used together with the **onFinish** parameter of **AnimateParam**. Its **radius** parameter must be set to **0** when the animation ends; otherwise, there may be unexpected results.
> 
> - When using this API, do not frequently change the blur radius of the same component; otherwise, there may be unexpected results. For example, if you frequently click the image in the example, the blur effect may not work sometimes.
> 
> - To avoid unexpected results, make sure the coordinates of the motion blur anchor point are the same as those of the animation scaling anchor point.
> 
> - To avoid unexpected results, set the blur radius to a value less than 1.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [MotionBlurOptions](arkts-arkui-common-comp-motionbluroptions-i.md) | Yes | Motion blur options. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="motionblur-1"></a>

## motionBlur

```TypeScript
motionBlur(motionBlur: Optional<MotionBlurOptions>): T
```

Applies a motion blur effect to the component being scaled or moved. Compared with [motionBlur](#motionblur), this API supports the **undefined** type for the **motionBlur** parameter.

1. Do not use this API in intra-component transitions, shared element transitions, implicit element transitions,
or particle animations. Doing so may cause unexpected results.

2. The **radius** parameter of **motionBlur** must be set to **0** for the initial state. Otherwise, there may be
unexpected results during a cold start.

3. This API must be used together with the **onFinish** parameter of **AnimateParam**. Its **radius** parameter
must be set to **0** when the animation ends; otherwise, there may be unexpected results.

4. When using this API, do not frequently change the blur radius of the same component; otherwise, there may be
unexpected results. For example, if you frequently click the image in the example, the blur effect may not work sometimes.

5. To avoid unexpected results, make sure the coordinates of the motion blur anchor point are the same as those
of the animation scaling anchor point.

6. To avoid unexpected results, set the blur radius to a value less than 1.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| motionBlur | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[MotionBlurOptions](arkts-arkui-common-comp-motionbluroptions-i.md)&gt; | Yes | Motion blur options.<br>If **motionBlur** is set to **undefined**, the previous value is retained. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## motionPath

```TypeScript
motionPath(value: MotionPathOptions): T
```

Sets a path animation for the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [MotionPathOptions](arkts-arkui-common-comp-motionpathoptions-i.md) | Yes | Motion path of the component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## mouseResponseRegion

```TypeScript
mouseResponseRegion(value: Array<Rectangle> | Rectangle): T
```

Sets one or more mouse response regions.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[Rectangle](arkts-arkui-common-comp-rectangle-i.md)&gt; &#124; [Rectangle](arkts-arkui-common-comp-rectangle-i.md) | Yes | Mouse response regions, defining the position and size.<br>The default touch target is the entire component. Default value:<br>{<br>x: 0,<br>y: 0,<br>width: '100%',<br> height: '100%'<br>} |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## nextFocus

```TypeScript
nextFocus(nextStep: Optional<FocusMovement>): T
```

Set nextFocus.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| nextStep | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[FocusMovement](arkts-arkui-common-comp-focusmovement-i.md)&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## obscured

```TypeScript
obscured(reasons: Array<ObscuredReasons>): T
```

Sets how the component content is obscured.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reasons | Array&lt;[ObscuredReasons](../arkts-apis/arkts-arkui-obscuredreasons-e.md)&gt; | Yes | How the component content is obscured.<br>This API is only available for the [Image](arkts-arkui-image-comp.md#image)<!--Del-->, [FormComponent](arkts-arkui-formcomponent-comp-sys.md#form_component)&lt;sup&gt;12+&lt;/sup&gt;,<!--DelEnd--> and [Text](arkts-arkui-text-comp.md#text) components.<br>**NOTE:** <br>To obscure an image when it is being loaded, you must set the width and height of the **Image** component.<br>Obscuring is not available for **Text** components that have child components or have any [styled string](../arkts-apis/arkts-arkui-styled_string.md) configured. <br>Default value: []. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Returns the current component. |

## offset

```TypeScript
offset(value: Position | Edges | LocalizedEdges): T
```

Sets the offset of the component relative to its original position. When **offset** is used in combination with the position attribute, the **position** attribute takes precedence and the configured offset will not be applied. This attribute supports dynamic configuration via [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position &#124; Edges &#124; [LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md) | Yes | Relative offset. The component is offset based on its original layout position. The **offset** attribute does not affect the parent component layout; it only adjusts the position during drawing. <br>The Position type is offset based on the top-left corner of the component itself, and the Edges type is offset based on the four edges of the component itself. Setting **{x: x, y: y}** for the **offset** attribute has the same effect as setting **{left: x, top: y}** and **{right: -x, bottom: -y}**. The [LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md) type supports mirroring mode: in LTR mode, **start** is equivalent to **x**; in RTL mode, **start** is equivalent to **-x**. <br>API version 9 and earlier: The default value is **{x: 0, y: 0}**. <br>Default unit: vp <br>API version 10: no default value. <br>When the value is abnormal, this attribute does not take effect.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onAccessibilityActionIntercept

```TypeScript
onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback): T
```

Register accessibility action intercept callback, when accessibility action is to be executed,the callback will be executed

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AccessibilityActionInterceptCallback](arkts-arkui-common-comp-accessibilityactioninterceptcallback-t.md) | Yes | accessibility action intercept callback function |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onAccessibilityFocus

```TypeScript
onAccessibilityFocus(callback: AccessibilityFocusCallback): T
```

Register accessibility focus callback,when the component is focused or out of focus,the callback will be executed

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AccessibilityFocusCallback](arkts-arkui-common-comp-accessibilityfocuscallback-t.md) | Yes | accessibility focus callback function |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onAccessibilityHover

```TypeScript
onAccessibilityHover(callback: AccessibilityCallback): T
```

Trigger a accessibility hover event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AccessibilityCallback](arkts-arkui-common-comp-accessibilitycallback-t.md) | Yes | A callback instance used when the component is touched after accessibility mode is enabled. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onAccessibilityHoverTransparent

```TypeScript
onAccessibilityHoverTransparent(callback: AccessibilityTransparentCallback): T
```

prompt for current component and descendants unable to handle accessibility hover event

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AccessibilityTransparentCallback](arkts-arkui-common-comp-accessibilitytransparentcallback-t.md) | Yes | A callback instance used when current component and descendants not handled accessibility hover event |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onAppear

```TypeScript
onAppear(event: () => void): T
```

Triggered when this component appears.

> **NOTE:** 
> 
> This callback may be called after the component layout and rendering process.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function of the **onAppear** event, which indicates that the component is displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onAreaChange

```TypeScript
onAreaChange(event: (oldValue: Area, newValue: Area) => void): T
```

Triggered when the component area changes in size or position due to layout updates.

This event is not triggered for render attribute changes caused by re-rendering, such as changes to [translate](#translate), [offset](#offset), [markAnchor](#markanchor), [scale](#scale), or [transform](#transform). In addition, if the component position is altered due to drawing changes, for example, through [bindSheet](#bindsheet), this event is also not triggered.

> **NOTE:** 
> 
> When a component is bound to both the **onAreaChange** event and the [position](#position)
> attribute, the **onAreaChange** event responds to changes in the **position** attribute of type
> Position, but does not respond to changes in the **position** attribute of type
> Edges or [LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (oldValue: Area, newValue: Area) =&gt; void | Yes | Position information of the target element. **oldValue** indicates the width and height of the target element as well as its coordinates relative to the parent element and the upper left corner of the page before the change. **newValue** indicates these dimensions and coordinates after the change. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="onareachange-1"></a>

## onAreaChange

```TypeScript
onAreaChange(event: AreaChangeCallback, options?: AreaChangeOptions): T
```

Triggered when the component area changes. The interval at which the callback is triggered can be set using expectedUpdateInterval in [AreaChangeOptions](arkts-arkui-common-comp-areachangeoptions-i.md). This event is triggered only in response to changes in component size or position caused by layout updates.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [AreaChangeCallback](arkts-arkui-common-comp-areachangecallback-t.md) | Yes | Callback function for the **onAreaChange** event. Triggered when the component's size or position changes. |
| options | [AreaChangeOptions](arkts-arkui-common-comp-areachangeoptions-i.md) | No | Parameters related to the area change. If not specified, **expectedUpdateInterval** is treated as **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onAttach

```TypeScript
onAttach(callback: Callback<void>): T
```

Triggered when this component is mounted to the component tree. Due to the following limitations, it is recommended that you use [onAppear](#onappear) instead of this callback.

> **NOTE:** 
> 
> - This callback is triggered before the component layout and rendering process.
> 
> - Modifying the component tree within the callback is prohibited, including initiating animations or altering the component structure through conditional statements like **if-else**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; | Yes | Callback function of the **onAttach** event, indicating that the component has been mounted to the component tree. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onAxisEvent

```TypeScript
onAxisEvent(event: Callback<AxisEvent>): T
```

Triggered by mouse wheel scrolling, a two-finger sliding gesture, or a pinch gesture on the touchpad.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[AxisEvent](arkts-arkui-common-comp-axisevent-i.md)&gt; | Yes | [AxisEvent](arkts-arkui-common-comp-axisevent-i.md) object. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onBlur

```TypeScript
onBlur(event: () => void): T
```

Triggered when the current component loses focus.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function of **onBlur**, which indicates that the component has lost focus. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onChildTouchTest

```TypeScript
onChildTouchTest(event: (value: Array<TouchTestInfo>) => TouchResult): T
```

Allows the current component to customize the hit test and control child component behavior during the test by setting a callback.

> **NOTE:** 
> 
> - The array of child node information only includes information about named nodes, that is, nodes for which the
> **id** attribute is explicitly set.
> 
> - This API can be called in [attributeModifier](#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (value: Array&lt;[TouchTestInfo](arkts-arkui-common-comp-touchtestinfo-c.md)&gt;) =&gt; TouchResult | Yes | Touch event information. **value**: array of child node information. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onClick

```TypeScript
onClick(event: (event: ClickEvent) => void): T
```

Called when a click event occurs.

When triggered by keyboard or gamepad input, the event's **SourceTool** is **Unknown**, and [SourceType](arkts-arkui-common-comp-sourcetype-e.md) is **KEY** or **JOYSTICK**.

> **NOTE:** 
> 
> Since API version 9, the following constraints apply when this API is used in service widgets:
> 
> 1. Click events will not be triggered if the finger is pressed for more than 800 ms.
> 
> 2. Click events will not be triggered if the finger moves more than 20 px after pressing down.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ClickEvent) =&gt; void | Yes | Callback for the click event. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="onclick-1"></a>

## onClick

```TypeScript
onClick(event: Callback<ClickEvent>, distanceThreshold: number): T
```

Called when a click event occurs.

When triggered by keyboard or gamepad input, the event's [SourceTool](arkts-arkui-common-comp-sourcetool-e.md) is **Unknown**, and [SourceType](arkts-arkui-common-comp-sourcetype-e.md) is **KEY** or **JOYSTICK**.

Compared with the original **onClick** API, this API has the **distanceThreshold** parameter that specifies the finger movement threshold for click events. If the finger's movement exceeds the set threshold, the gesture recognition will fail. The click gesture recognition will fail if finger movement exceeds this threshold.

For scenarios where there is no restriction on the finger movement distance during a click, the original API is preferred. To limit finger movement range during a click, use this new API.

> **NOTE:** 
> 
> - Since API version 12, the following constraints apply when this API is used in service widgets:
> 
> 1. Click events will not be triggered if the finger is pressed for more than 800 ms.
> 
> 2. Click events will not be triggered if the finger moves more than 20 px after pressing down.
> 
> - This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[ClickEvent](arkts-arkui-common-comp-clickevent-i.md)&gt; | Yes | Callback for the click event. |
| distanceThreshold | number | Yes | Finger movement threshold for click events. If the value specified is less than or equal to 0, it will be converted to the default value.<br>Default value: 2^31-1<br>Unit: vp<br>**NOTE:** <br>If the finger movement exceeds the preset movement threshold, the gesture recognition fails. If the default threshold is used during initialization and the finger moves beyond the component's touch target, the gesture recognition fails. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDetach

```TypeScript
onDetach(callback: Callback<void>): T
```

Triggered when this component is unmounted from the component tree. You are advised to use [onDisAppear](#ondisappear) instead.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; | Yes | Callback function of the **onDetach** event, indicating that the component has been unmounted from the component tree. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDigitalCrown

```TypeScript
onDigitalCrown(handler: Optional<Callback<CrownEvent>>): T
```

Called when the crown is rotated while the component has focus.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Callback](arkts-arkui-common-comp-callback-i.md)&lt;[CrownEvent](arkts-arkui-common-comp-crownevent-i.md)&gt;&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDisAppear

```TypeScript
onDisAppear(event: () => void): T
```

Triggered when this component disappears.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function of the **onDisAppear** event, which indicates that the component is hidden. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDragEnd

```TypeScript
onDragEnd(event: (event: DragEvent, extraParams?: string) => void): T
```

Triggered when the dragging of the component bound to the event ends.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | Yes | Callback function.<br>**NOTE:** <br> **event**: drag event information. The coordinates of the drag point are not included in **onDragEnd**.<br> **extraParams**: additional information about the drag event. Its value must be parsed into JSON format. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDragEnter

```TypeScript
onDragEnter(event: (event: DragEvent, extraParams?: string) => void): T
```

Triggered when a dragged item enters a valid drop target. This event takes effect only when a listener for the [onDrop](#ondrop) event is enabled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | Yes | Callback function.<br>**NOTE:** <br> **event**: drag event information, including the coordinates of the drag point.<br> **extraParams**: additional information about the drag event. Its value must be parsed into JSON format. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDragLeave

```TypeScript
onDragLeave(event: (event: DragEvent, extraParams?: string) => void): T
```

Triggered when a dragged item leaves a valid drop target. This event takes effect only when a listener for the [onDrop](#ondrop) event is enabled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | Yes | Callback function.<br>**NOTE:** <br> **event**: drag event information, including the coordinates of the drag point.<br> **extraParams**: additional information about the drag event. Its value must be parsed into JSON format. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDragMove

```TypeScript
onDragMove(event: (event: DragEvent, extraParams?: string) => void): T
```

Triggered when a dragged item moves in a valid drop target. This event takes effect only when a listener for the [onDrop](#ondrop) event is enabled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | Yes | Callback function.<br>**NOTE:** <br> **event**: drag event information, including the coordinates of the drag point.<br> **extraParams**: additional information about the drag event. Its value must be parsed into JSON format. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDragSpringLoading

```TypeScript
onDragSpringLoading(callback: Callback<SpringLoadingContext> | null, configuration?: DragSpringLoadingConfiguration): T
```

The component bound to this event can be used as a drag-response target with hover detection capability. When the dragged object hovers over the target, the callback is triggered. Only one target can become the responder at any time, and child components always have higher response priority.

For details about the hover detection triggering mechanism and usage, see [Spring Loading (Hover Detection) Support](../../../ui/arkts-common-events-drag-event.md#spring-loading-hover-detection-support).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[SpringLoadingContext](arkts-arkui-common-comp-springloadingcontext-t.md)&gt; &#124; null | Yes | Hover detection callback. If the value is **null**, hover detection is disabled. |
| configuration | [DragSpringLoadingConfiguration](arkts-arkui-common-comp-dragspringloadingconfiguration-t.md) | No | Hover detection configuration. If the value is **undefined**, the default value of [DragSpringLoadingConfiguration](../arkts-apis/arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md) is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDragStart

```TypeScript
onDragStart(event: (event: DragEvent, extraParams?: string) => CustomBuilder | DragItemInfo): T
```

In a gesture-based drag scenario, this callback is triggered when a user long-presses a draggable component for more than 500 ms and then moves the finger more than 10 vp. In a mouse-drag scenario, it is triggered when the left mouse button is pressed on a draggable component and moved more than 1 vp.

For components that provide drag and drop capabilities by default, a custom **onDragStart** event, if set, is executed and:

- If a custom drag preview is returned, it is used in place of the default drag preview.  
- If drag data is set, it is used in place of the default drag data.

The custom drag preview is not supported for dragging selected text in the following components: Text, Search, TextInput, TextArea, RichEditor When **onDragStart** is used with menu preview or any component that provides default drag and drop capabilities, custom content on menu items and the preview cannot be dragged.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](#attributemodifier) since API version 13.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; CustomBuilder &#124; DragItemInfo | Yes | Callback function.<br> **NOTE:** <br> **event**: drag event information.<br> **extraParams**: additional information about the drag event. Its value must be parsed into JSON format.<br> **CustomBuilder**: component information displayed during dragging. Global builders are not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onDrop

```TypeScript
onDrop(event: (event: DragEvent, extraParams?: string) => void): T
```

A component bound with this event can serve as a drop target. This callback is triggered when the drag-and-drop action stops within the bounds of this component If **event.setResult()** is not explicitly called in the **onDrop** callback to set the drag-and-drop result, then: For supported components, the result is determined based on the actual data processed; for other components, the system considers the data as successfully received.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: DragEvent, extraParams?: string) =&gt; void | Yes | Callback function.<br>**NOTE:** <br> **event**: drag event information, including the coordinates of the drag point.<br> **extraParams**: additional information about the drag event. Its value must be parsed into JSON format. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="ondrop-1"></a>

## onDrop

```TypeScript
onDrop(eventCallback: OnDragEventCallback, dropOptions?: DropOptions): T
```

Triggered when a dragged item is dropped on a valid drop target. If you do not explicitly call event. [setResult](arkts-arkui-common-comp-dragevent-i.md#setresult)() in **onDrop** to set the result of the drag reception, the system handles it as follows:

- If the component being dragged is one that supports drop actions by default, the system's actual data processing  
result is used.  
- For other components, the system assumes that the data is received successfully.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventCallback | [OnDragEventCallback](arkts-arkui-common-comp-ondrageventcallback-t.md) | Yes | Callback function. |
| dropOptions | [DropOptions](arkts-arkui-common-comp-dropoptions-i.md) | No | Parameters for the drop process. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onFocus

```TypeScript
onFocus(event: () => void): T
```

Triggered when the current component obtains focus.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback function of **onFocus**, indicating that the component has gained focus. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onFocusAxisEvent

```TypeScript
onFocusAxisEvent(event: Callback<FocusAxisEvent>): T
```

Binds a focus axis event callback to the component. Triggered when any operation is performed with the game controller's directional pad or joystick on the bound component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[FocusAxisEvent](arkts-arkui-common-comp-focusaxisevent-i.md)&gt; | Yes | Focus axis event callback. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onGestureCollectIntercept

```TypeScript
onGestureCollectIntercept(callback: GestureCollectInterceptCallback): T
```

Triggered after events and gestures on the current node and higher-priority nodes are collected. This callback can be used to intervene in the collection results of events and gestures. This callback uses an asynchronous callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [GestureCollectInterceptCallback](arkts-arkui-common-comp-gesturecollectinterceptcallback-t.md) | Yes | A callback instance used when the component does a touch test. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onGestureJudgeBegin

```TypeScript
onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T
```

Binds a custom gesture determination callback to the component. When the gesture is about to succeed, the user- defined callback is triggered to obtain the result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (gestureInfo: GestureInfo, event: BaseGestureEvent) =&gt; GestureJudgeResult | Yes | A callback instance used when a gesture bound to this component will be accepted. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onGestureRecognizerJudgeBegin

```TypeScript
onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback): T
```

Binds a custom gesture recognizer judgment callback to the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [GestureRecognizerJudgeBeginCallback](arkts-arkui-common-comp-gesturerecognizerjudgebegincallback-t.md) | Yes | A callback instance used when a gesture bound to this component will be accepted. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="ongesturerecognizerjudgebegin-1"></a>

## onGestureRecognizerJudgeBegin

```TypeScript
onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback, exposeInnerGesture: boolean): T
```

Binds a custom gesture recognizer judgment callback to the component.

The **exposeInnerGesture** parameter indicates whether to expose gestures from built-in components within ArkUI system composite components to developers. When this parameter is set to **true**, these internal gestures are exposed.

For scenarios where exposure of internal gestures is not required, use the original [onGestureRecognizerJudgeBegin](#ongesturerecognizerjudgebegin) API. Use this API with **exposeInnerGesture** set to **true** only when internal gesture exposure is necessary.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [GestureRecognizerJudgeBeginCallback](arkts-arkui-common-comp-gesturerecognizerjudgebegincallback-t.md) | Yes | A callback instance used when a gesture bound to this component will be accepted. |
| exposeInnerGesture | boolean | Yes | This parameter is a flag. This flag determines whether to expose internal gestures. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onHover

```TypeScript
onHover(event: (isHover: boolean, event: HoverEvent) => void): T
```

Triggered when the mouse pointer or stylus enters or leaves the component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (isHover: boolean, event: HoverEvent) =&gt; void | Yes | Callback for mouse or stylus hover status.<br>**event**: event bubbling control and coordinates of the hover position; available since API version 11.<br>**isHover**: whether the mouse pointer or stylus is hovering over the component. **true**: The mouse pointer or stylus has entered the component. **false**: The mouse pointer or stylus has left the component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onHoverMove

```TypeScript
onHoverMove(event: Callback<HoverEvent>): T
```

Triggered when a stylus hovers over the component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[HoverEvent](arkts-arkui-common-comp-hoverevent-i.md)&gt; | Yes | Callback that controls event bubbling blocking and obtains the stylus hover position coordinates. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onKeyEvent

```TypeScript
onKeyEvent(event: (event: KeyEvent) => void): T
```

Triggered when a key event occurs.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: KeyEvent) =&gt; void | Yes | **KeyEvent** object. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="onkeyevent-1"></a>

## onKeyEvent

```TypeScript
onKeyEvent(event: Callback<KeyEvent, boolean>): T
```

Triggered when a key operation is performed on the bound component after it obtains focus. If the callback returns **true**, the key event is considered handled.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[KeyEvent](arkts-arkui-common-comp-keyevent-i.md), boolean&gt; | Yes | Callback for handling the key event. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onKeyEventDispatch

```TypeScript
onKeyEventDispatch(event: Callback<KeyEvent, boolean>): T
```

Triggered when the bound component receives a key event. The key event will not be dispatched to its child components. Only existing key events can be intercepted; creating new **KeyEvent** objects for dispatch is not supported.

If the callback returns **true**, the key event is marked as consumed and will not [bubble up](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) to parent components.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[KeyEvent](arkts-arkui-common-comp-keyevent-i.md), boolean&gt; | Yes | Callback for handling key event dispatch. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onKeyPreIme

```TypeScript
onKeyPreIme(event: Callback<KeyEvent, boolean>): T
```

Triggered before other callbacks when a key operation is performed on the bound component after it obtains focus.

If the return value of this callback is **true**, the key event is considered consumed, and subsequent event callbacks (**keyboardShortcut**, input method events, **onKeyEventDispatch**, and **onKeyEvent**) will be intercepted and no longer triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[KeyEvent](arkts-arkui-common-comp-keyevent-i.md), boolean&gt; | Yes | Callback for handling the key event. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onMouse

```TypeScript
onMouse(event: (event: MouseEvent) => void): T
```

Triggered when the component is clicked by a mouse button or the mouse pointer moves on the component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: MouseEvent) =&gt; void | Yes | Timestamp, mouse button, action, coordinates of the clicked point on the entire screen, and coordinates of the clicked point relative to the component when the event is triggered. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onNeedSoftkeyboard

```TypeScript
onNeedSoftkeyboard(onNeedSoftkeyboardCallback: OnNeedSoftkeyboardCallback | undefined): T
```

Called when component is focused, the return value indicates whether keyboard is needed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| onNeedSoftkeyboardCallback | [OnNeedSoftkeyboardCallback](arkts-arkui-common-comp-onneedsoftkeyboardcallback-t.md) &#124; undefined | Yes | Callback executed when an event is triggered. The system determines whether a keyboard is required based on the return value of the callback. If this parameter is set to undefined, no callback is triggered, and the input box component returns true. For other components, false is returned. Prerequisite: The component must be able to obtain focus. Otherwise, this interface does not take effect. When the return value is true, the self-drawn text box needs to actively invoke the [attach](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod-inputmethodcontroller-i.md#attach-2) method to establish input method communication when the focus is obtained. Otherwise, the keyboard does not respond. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## onPreDrag

```TypeScript
onPreDrag(callback: Callback<PreDragStatus>): T
```

Triggered when the component enters a state prior to a gesture-based drag operation. For details about the state prior to the drag-and-drop operation, see [PreDragStatus](arkts-arkui-common-comp-predragstatus-e.md). This API cannot be triggered in mouse-based drag scenarios.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[PreDragStatus](arkts-arkui-common-comp-predragstatus-e.md)&gt; | Yes | Callback function. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onSizeChange

```TypeScript
onSizeChange(event: SizeChangeCallback): T
```

Triggered when the component size changes due to layout updates.

> **NOTE:** 
> 
> 1. This API is triggered upon layout changes. Due to calculation precision limitations, the return value may deviate slightly from the actual physical size.
> 
> 2. **onSizeChange** is a synchronous callback triggered during the layout process. Directly modifying state variables within **onSizeChange** may cause the changes to be included in the animation closure. Specifically,animations compare the layout state before the animation starts with the state after the animation closure is executed. If the **onSizeChange** callback is triggered synchronously during the pre-animation layout phase, the changes made in this callback will be processed as part of the animation, along with the changes in the animation closure. To avoid this issue, you can use [setTimeout](../arkts-apis/arkts-arkui-global-settimeout-f.md) or [postFrameCallback](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#postframecallback) (with a 0 ms delay) inside
> **onSizeChange** to defer the UI processing logic to asynchronous execution.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [SizeChangeCallback](arkts-arkui-common-comp-sizechangecallback-t.md) | Yes | Size of the component before and after the change. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onTouch

```TypeScript
onTouch(event: (event: TouchEvent) => void): T
```

Invoked when a touch event is triggered. Touch events [bubble](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) by default and can be consumed by multiple components. To prevent event bubbling, use the **stopPropagation** API of [TouchEvent](arkts-arkui-common-comp-touchevent-i.md). Mouse left-click events are converted to touch events and will also trigger this callback.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: TouchEvent) =&gt; void | Yes | **TouchEvent** object. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onTouchIntercept

```TypeScript
onTouchIntercept(callback: Callback<TouchEvent, HitTestMode>): T
```

Binds a custom event interception callback to a component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[TouchEvent](arkts-arkui-common-comp-touchevent-i.md), [HitTestMode](../arkts-apis/arkts-arkui-hittestmode-e.md)&gt; | Yes | Custom event interception callback. Triggered during hit testing and sets the hit test behavior for the component based on the return value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onTouchTestDone

```TypeScript
onTouchTestDone(callback: TouchTestDoneCallback): T
```

Specifies whether gesture recognizers participate in subsequent processing after [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) completes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [TouchTestDoneCallback](arkts-arkui-common-comp-touchtestdonecallback-t.md) | Yes | Callback to specify gesture recognizer participation in subsequent processing. Triggered after [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) completes but before user gesture recognition begins. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onVisibleAreaApproximateChange

```TypeScript
onVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): T
```

Configures a callback for the **onVisibleAreaApproximateChange** event, with options to limit the callback execution interval.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 23.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-arkui-common-comp-visibleareaeventoptions-i.md) | Yes | Visible area change configuration options. |
| event | [VisibleAreaChangeCallback](arkts-arkui-common-comp-visibleareachangecallback-t.md) &#124; undefined | Yes | Callback for the **onVisibleAreaChange** event. This callback is triggered when the ratio of the component's visible area to its total area approaches the threshold set in **options**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onVisibleAreaChange

```TypeScript
onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback): T
```

Called when the visible area of the component changes. For details about the development guidelines and FAQs, see [Detecting Component Visibility](../../../ui/arkts-manage-components-visibility.md).

> **NOTE:** 
> 
> - This API can be called in [attributeModifier](#attributemodifier) since API version 20.
> 
> - This API only takes into account the relative clipped area ratio of the component with respect to all ancestor nodes (up to the window boundary) and its own area.
> 
> - The following calculation scenarios are not supported: clipping by sibling nodes, clipping by siblings of any ancestor node, window-level occlusion, and component rotation. Examples include layouts using [Stack](../../apis-default/arkts-apis/arkts-lib-es5-error-i.md#stack), [z-order control](#zindex), and [rotate](#rotate) transformations.
> 
> - It does not support visibility change calculations for nodes that are not in the component tree. For example,preloaded nodes or custom nodes mounted using the [overlay](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-overlay.md#overlay) capability.
> 
> - This API does not support the [scale](#scale) attribute. To enable support for the [scale](#scale) attribute, use [onVisibleAreaChange&lt;sup&gt;22+&lt;/sup&gt;](#onvisibleareachange-1)and set **measureFromViewport** to **true**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratios | Array&lt;number&gt; | Yes | Threshold array. Each threshold represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. This callback is invoked when the ratio of the component's visible area to its total area is greater than or less than the threshold. The value of each threshold ranges from 0.0 to 1.0. If a threshold value is less than 0.0, it is clamped to 0.0; if it is greater than 1.0, it is clamped to 1.0.<br>**NOTE:** <br>When the value is close to the boundary 0 or 1, it is rounded off with a round-off error not greater than 0.001. For example, 0.9997 is rounded off to 1. |
| event | [VisibleAreaChangeCallback](arkts-arkui-common-comp-visibleareachangecallback-t.md) | Yes | Callback for visible area changes of the component.<br>**Since:** 13 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="onvisibleareachange-1"></a>

## onVisibleAreaChange

```TypeScript
onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback, measureFromViewport: boolean): T
```

Called when the visible area of the component changes. You can use **measureFromViewport** to set the visible area calculation mode. For details about the development guidelines and FAQs, see [Detecting Component Visibility](../../../ui/arkts-manage-components-visibility.md).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratios | Array&lt;number&gt; | Yes | Threshold array. Each threshold represents the ratio of the component's visible area to its own total area. This callback is invoked when the ratio of the component's visible area to its total area is greater than or less than the threshold. The value of each threshold ranges from 0.0 to 1.0. If a threshold value is less than 0.0, it is clamped to 0.0; if it is greater than 1.0, it is clamped to 1.0.<br> **NOTE:** <br>When the value is close to the boundary 0 or 1, it is rounded off with a round-off error not greater than 0.001. For example, 0.9997 is rounded off to 1. |
| event | [VisibleAreaChangeCallback](arkts-arkui-common-comp-visibleareachangecallback-t.md) | Yes | Callback for visible area changes of the component. |
| measureFromViewport | boolean | Yes | Visible area calculation mode.<br>**true**: considers the parent's [clip](#clip) attribute. If [clip](#clip) is **false**, areas of the child component beyond the parent's bounds are counted as visible; if [clip](#clip) is **true**, such areas are counted as invisible. **false**: ignores the parent's [clip](#clip) attribute, treating areas beyond the parent's bounds as invisible.<br>When **measureFromViewport** is set to **true**, and an ancestor node has the [scale](#scale) attribute set, the component's visible ratio will be correctly calculated. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## opacity

```TypeScript
opacity(value: number | Resource): T
```

Sets the opacity of the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Component opacity. Value range: 0 to 1. Values less than 0 are treated as 0. Values greater than 1 are treated as 1. **1**: fully opaque. **0**: fully transparent (where the component is hidden but occupies layout space).<br> Default value: **1**.<br>**NOTE:** <br> Child components inherit parent opacity and combine with their own opacity. Example: Parent opacity 0.1 x Child opacity 0.8 = Effective opacity 0.08. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="opacity-1"></a>

## opacity

```TypeScript
opacity(opacity: Optional<number | Resource>): T
```

Sets the opacity of the component. Compared with [opacity](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-opacity.md#opacity), this API supports the **undefined** type for the **opacity** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| opacity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)&gt; | Yes | Component opacity. Value range: 0 to 1. Values less than 0 are treated as 0. Values greater than 1 are treated as 1. **1**: fully opaque. **0**: fully transparent (where the component is hidden but occupies layout space).<br> Default value: **1**.<br>**NOTE:** <br> Child components inherit parent opacity and combine with their own opacity. Example: Parent opacity 0.1 x Child opacity 0.8 = Effective opacity 0.08.<br>When **opacity** is **undefined**, the component reverts to the default opacity of **1**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## outline

```TypeScript
outline(value: OutlineOptions): T
```

Sets the outline attributes in one declaration.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [OutlineOptions](../arkts-apis/arkts-arkui-outlineoptions-i.md) | Yes | Outline attributes. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="outline-1"></a>

## outline

```TypeScript
outline(options: Optional<OutlineOptions>): T
```

Sets the outline attributes in one declaration. Compared with [outline](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-outline.md#outline), this API supports the **undefined** type for the **options** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OutlineOptions](../arkts-apis/arkts-arkui-outlineoptions-i.md)&gt; | Yes | Outline attributes.<br>If **options** is **undefined**, the component reverts to its original style with no outline. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## outlineColor

```TypeScript
outlineColor(value: ResourceColor | EdgeColors | LocalizedEdgeColors): T
```

Sets the outline color. If this API is not used, the default color black will be applied.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](../arkts-apis/arkts-arkui-localizededgecolors-i.md) | Yes | Outline color.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="outlinecolor-1"></a>

## outlineColor

```TypeScript
outlineColor(color: Optional<ResourceColor | EdgeColors | LocalizedEdgeColors>): T
```

Sets the outline color. If this API is not used, the default color black will be applied. Compared with [outlineColor](#outlinecolor), this API supports the **undefined** type for the **color** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; EdgeColors &#124; [LocalizedEdgeColors](../arkts-apis/arkts-arkui-localizededgecolors-i.md)&gt; | Yes | Outline color.<br>If **color** is **undefined**, the component reverts to its original style with the outline color of **Color.Black**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## outlineRadius

```TypeScript
outlineRadius(value: Dimension | OutlineRadiuses): T
```

Sets the radius of the outline corners. If this API is not used, there will be no change by default.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; OutlineRadiuses | Yes | Radius of the outline corners. Percentage values are not supported.<br>Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="outlineradius-1"></a>

## outlineRadius

```TypeScript
outlineRadius(radius: Optional<Dimension | OutlineRadiuses>): T
```

Sets the radius of the outline corners. If this API is not used, there will be no change by default. Compared with [outlineRadius](#outlineradius), this API supports the **undefined** type for the **radius** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; OutlineRadiuses&gt; | Yes | Radius of the outline corners. Percentage values are not supported.<br>Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth<br>If **radius** is **undefined**, the component reverts to its original style with the outline corner radius of 0. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## outlineStyle

```TypeScript
outlineStyle(value: OutlineStyle | EdgeOutlineStyles): T
```

Sets the outline style. If this API is not used, a solid line is displayed by default.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [OutlineStyle](arkts-arkui-common-comp-outlinestyle-e.md) &#124; EdgeOutlineStyles | Yes | Outline style. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="outlinestyle-1"></a>

## outlineStyle

```TypeScript
outlineStyle(style: Optional<OutlineStyle | EdgeOutlineStyles>): T
```

Sets the outline style. If this API is not used, a solid line is displayed by default. Compared with [outlineStyle](#outlinestyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OutlineStyle](arkts-arkui-common-comp-outlinestyle-e.md) &#124; EdgeOutlineStyles&gt; | Yes | Outline style.<br>If **style** is **undefined**, the component reverts to its original style with no outline. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## outlineWidth

```TypeScript
outlineWidth(value: Dimension | EdgeOutlineWidths): T
```

Sets the thickness of the outline. If this API is not used, there will be no change by default.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; EdgeOutlineWidths | Yes | Outline thickness. Percentage values are not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="outlinewidth-1"></a>

## outlineWidth

```TypeScript
outlineWidth(width: Optional<Dimension | EdgeOutlineWidths>): T
```

Sets the thickness of the outline. If this API is not used, there will be no change by default. Compared with [outlineWidth](#outlinewidth), this API supports the **undefined** type for the **width** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; EdgeOutlineWidths&gt; | Yes | Outline thickness. Percentage values are not supported.<br>If **width** is **undefined**, the component reverts to its original style with no outline width. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## overlay

```TypeScript
overlay(value: string | CustomBuilder | ComponentContent, options?: OverlayOptions): T
```

Adds an overlay to this component, which can be text, a custom component, or [ComponentContent](arkts-arkui-common-comp-componentcontent-t.md). The overlay is positioned based on the current component. The overlay is not rendered through the component tree, meaning some APIs (for example, [getRectangleById](../arkts-apis/arkts-arkui-componentutils-getrectanglebyid-f.md)) cannot access components within the overlay.

> **NOTE:** 
> 
> The overlay places the floating layer component above the bound component, blocking all user interactions with
> components beneath it. To enable interaction with underlying components, refer to
> [Example 2: Setting an Overlay Using a Custom Builder](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-overlay.md#example-2-setting-an-overlay-using-a-custom-builder)
> and apply **.hitTestBehavior(HitTestMode.Transparent)** to the outermost component in the overlay builder. This
> configuration is particularly crucial for watermark implementations, where the overlay must not interfere with
> user interaction with the underlying content.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [ComponentContent](arkts-arkui-common-comp-componentcontent-t.md) | Yes | Content of the overlay, which can be text or a custom component.<br>**NOTE:** <br>When the overlay is a custom component, it cannot obtain focus through sequential keyboard navigation. Using **CustomBuilder** will cause the overlay content to be destroyed and recreated on page refresh, which may incur performance overhead. For scenarios with frequent page updates, using **ComponentContent** is recommended.<br>**Since:** 12 |
| options | [OverlayOptions](arkts-arkui-common-comp-overlayoptions-i.md) | No | Options for positioning the overlay.<br>**NOTE:** <br>In versions earlier than API version 12, **options** is defined as follows:<br>{<br>align?: [Alignment](../arkts-apis/arkts-arkui-alignment-e.md), <br>offset?: {x?: number, y?: number}<br>}<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## padding

```TypeScript
padding(value: Padding | Length | LocalizedPadding): T
```

Sets the padding attribute of the component. After the setting, extra space is created between the component content and the border, affecting the layout area of the component's internal content. <br>Since API version 10, this API supports the calc calculation feature.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Padding &#124; [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | Yes | Padding of the component.<br>When the parameter is of the **Length** type, the padding takes effect on all four sides simultaneously.<br>Default value: **0** <br>Unit: vp <br> When padding is set to a percentage, the padding on all four sides uses the **width** of the parent container as the base value.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## parallelGesture

```TypeScript
parallelGesture(gesture: GestureType, mask?: GestureMask): T
```

Gesture that can be recognized at once by the component and its child component. The gesture event is not a bubbling event. When **parallelGesture** is set for a component, both it and its child component can respond to the same gesture events, thereby implementing a quasi-bubbling effect.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | GestureType | Yes | Gesture object to bind. |
| mask | [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | No | Mask for gesture events.<br>Default value: **GestureMask.Normal**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## pixelRound

```TypeScript
pixelRound(value: PixelRoundPolicy): T
```

Specifies the pixel rounding alignment mode of the current component in the specified direction. After this attribute is set, the boundary coordinates of the component are rounded according to the specified strategy, thereby avoiding visual anomalies caused by floating-point rendering (such as 1px gaps, overlapping components, and disappearing dividers). Since API version 12, if a direction is not set, the pixels are rounded to the nearest whole number in that direction by default.

> **NOTE:** 
> 
> - In API version 11, this API uses half-pixel alignment (that is, 0~0.25 rounds to 0, 0.25~0.75 rounds to 0.5,0.75~1.0 rounds to 1). This mode reduces the cumulative error that may result from continuous rounding by preserving the 0.5 pixel value. Since API version 12, the direction for which no rounding strategy is set uses rounding to the nearest whole number by default, and pixel rounding in a specified direction can be disabled through PixelRoundCalcPolicy.NO_FORCE_ROUND.
> 
> - Since API version 12, this API can be called in [attributeModifier](#attributemodifier).

In normal calculations, the vertical direction (top and bottom) corresponds to the component height. In a left-to-right layout, start corresponds to the left direction and end corresponds to the right direction; in a mirrored layout (right-to-left), the correspondence is reversed. The horizontal direction (left and right) corresponds to the component width. For ease of description, the two groups of directions are referred to as top-left and bottom-right.

- Calculate the top-left coordinates of the current component: the offset of the top-left corner relative to the  
parent container.  
- Calculate the bottom-right coordinates of the current component: offset of the top-left corner relative to the  
parent container plus the size of the component itself.  
- Recalculate the size of the current component: rounded bottom-right coordinates minus rounded top-left  
coordinates (API version 11 uses half-pixel alignment, and API version 12 uses rounding to the nearest whole number).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PixelRoundPolicy](arkts-arkui-common-comp-pixelroundpolicy-i.md) | Yes | Boundary rounding strategy of the current component. [PixelRoundPolicy](arkts-arkui-common-comp-pixelroundpolicy-i.md) contains four optional attributes: start, top, end, and bottom, which correspond to the front, top, end, and bottom boundaries of the component, respectively. Each attribute can be set to a [PixelRoundCalcPolicy](../arkts-apis/arkts-arkui-pixelroundcalcpolicy-e.md) enum value. Setting PixelRoundCalcPolicy.NO_FORCE_ROUND disables pixel rounding in the corresponding direction. Attributes that are not set are rounded by default using the round-half-up rule. <br>**NOTE:** <br> This attribute is used in scenarios where floating-point drawing causes visual anomalies. Since API version 12, the round-half-up rounding method is used; API version 11 uses half-pixel alignment. The rounding result is related not only to the width and height of the component, but also to its position. Even if the width and height set for components are the same, the final width and height of the components after rounding may differ because the component positions described by floating-point numbers are different. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## pixelStretchEffect

```TypeScript
pixelStretchEffect(options: PixelStretchEffectOptions): T
```

Applies a pixel stretch effect to the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PixelStretchEffectOptions](arkts-arkui-common-comp-pixelstretcheffectoptions-i.md) | Yes | Pixel stretch effect options.<br>The value includes the length by which a pixel is stretched toward the four edges.<br>**NOTE:** <br>1. If the length is a positive value, the original image is stretched, and the image size increases. The edge pixels grow by the set length toward the top, bottom, left, and right edges.<br>2. If the length is a negative value, the original image shrinks as follows, but the image size remains unchanged:<br>Shrinking mode:<br>(1) The image shrinks from the four edges by the absolute value of length set through **options**.<br>(2) The image is stretched back to the original size with edge pixels.<br>3. Constraints on **options**:<br>(1) The length values for the four edges must be all positive or all negative. That is, the four edges are stretched or shrink at the same time in the same direction.<br>(2) The length values must all be a percentage or a specific value. Combined use of the percentage and specific value is not allowed.<br>If the input value is invalid, the image is displayed as {0, 0, 0, 0}, that is, the image remains unchanged. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="pixelstretcheffect-1"></a>

## pixelStretchEffect

```TypeScript
pixelStretchEffect(options: Optional<PixelStretchEffectOptions>): T
```

Applies a pixel stretch effect to the component. Compared to [pixelStretchEffect&lt;sup&gt;12+&lt;/sup&gt;](#pixelstretcheffect), the **options** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PixelStretchEffectOptions](arkts-arkui-common-comp-pixelstretcheffectoptions-i.md)&gt; | Yes | Pixel stretch effect options.<br>The value includes the length by which a pixel is stretched toward the four edges.<br>**NOTE:** <br>1. If the length is a positive value, the original image is stretched, and the image size increases. The edge pixels grow by the set length toward the top, bottom, left, and right edges.<br>2. If the length is a negative value, the original image shrinks as follows, but the image size remains unchanged:<br>Shrinking mode:<br>(1) The image shrinks from the four edges by the absolute value of length set through **options**.<br>(2) The image is stretched back to the original size with edge pixels.<br>3. Constraints on **options**:<br>(1) The length values for the four edges must be all positive or all negative. That is, the four edges are stretched or shrink at the same time in the same direction.<br>(2) The length values must all be a percentage or a specific value. Combined use of the percentage and specific value is not allowed.<br>If the input value is invalid, the image is displayed as {0, 0, 0, 0}, that is, the image remains unchanged.<br>If **options** is **undefined**, the component reverts to its original effect with no pixel stretch. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## position

```TypeScript
position(value: Position | Edges | LocalizedEdges): T
```

Sets the absolute positioning, which determines the position of a child component relative to the content area of the parent component. Dynamic configuration via [attributeModifier](#attributemodifier) is supported.

> **NOTE:** 
> 
> - The effect of **position** on the position takes effect after the component's size measurement is complete.
> - When the parent component is Row, Column, or Flex, a child component with **position** set does not occupy space. In this scenario, if all child components contained in the parent component have **position** set, the parent component's size cannot be determined by other child components, and layout measurement is performed based on the size (0, 0).
> - The Position type determines the position based on the upper left corner of the parent component's content area. The Edges type determines the position based on the four edges of the parent component's content area, where **top**, **left**, **right**, and **bottom** are the distances from each edge of the component to the corresponding edge of the parent component's content area, and the component's position relative to the parent component's content area is determined by these distances. The [LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md) type determines the position based on the four edges of the parent component's content area and supports mirroring mode.
> - This attribute is applicable to scenarios where components such as top-displayed elements and floating buttons have fixed positions within the parent component.
> - This attribute is not supported on layout components with zero width and height.
> - When the parent component is RelativeContainer and the child component has the [alignRules](#alignrules) attribute set, the child component's **position** attribute does not take effect.
> - If the parent component of the component where this attribute is located does not have a fixed width and height, this component performs absolute positioning with reference to the first ancestor component that has a fixed width and height.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Position &#124; Edges &#124; [LocalizedEdges](../arkts-apis/arkts-arkui-localizededges-i.md) | Yes | Absolute positioning that determines the child component's position relative to the parent's content area. The content area of the parent component is calculated by subtracting the [border](#border), padding, and [safeAreaPadding](#safeareapadding) values from the parent component's total size. This resulting content area defines the available layout space for child components. This attribute does not take effect when it is set to an abnormal value.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## priorityGesture

```TypeScript
priorityGesture(gesture: GestureType, mask?: GestureMask): T
```

Gesture to preferentially recognize.

1. By default, the child component preferentially recognizes the gesture specified by **gesture**, and the parent
component preferentially recognizes the gesture specified by **priorityGesture** (if set).
2. For long press gestures, the component with the shortest minimum hold-down time responds first, ignoring the  
**priorityGesture** settings.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | GestureType | Yes | Gesture object to bind. |
| mask | [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | No | Mask for gesture events.<br>Default value: **GestureMask.Normal**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## radialGradient

```TypeScript
radialGradient(value: RadialGradientOptions): T
```

Radial Gradient center:Center point of radial gradient radius:Radius of Radial Gradient. value range [0, +∞) colors:Color description for gradients repeating: Refill. The default value is false

Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RadialGradientOptions](arkts-arkui-common-comp-radialgradientoptions-i.md) | Yes | <br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="radialgradient-1"></a>

## radialGradient

```TypeScript
radialGradient(options: Optional<RadialGradientOptions>): T
```

Radial Gradient center:Center point of radial gradient radius:Radius of Radial Gradient. value range [0, +∞) colors:Color description for gradients repeating: Refill. The default value is false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[RadialGradientOptions](arkts-arkui-common-comp-radialgradientoptions-i.md)&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## renderFit

```TypeScript
renderFit(fitMode: RenderFit): T
```

Sets how the final state of the component's content is rendered during its width and height animation process. If it is not set via this API, the content size at the end of the animation is maintained, and the content always remains top-left aligned with the component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fitMode | [RenderFit](../arkts-apis/arkts-arkui-renderfit-e.md) | Yes | Sets how the final state of the component's content is rendered during its width and height animation process. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="renderfit-1"></a>

## renderFit

```TypeScript
renderFit(fitMode: Optional<RenderFit>): T
```

Sets how the final state of the component's content is rendered during its width and height animation process. If it is not set via this API, the content size at the end of the animation is maintained, and the content always remains top-left aligned with the component. Compared to [renderFit](#renderfit), this API supports the **undefined** type for the **fitMode** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fitMode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[RenderFit](../arkts-apis/arkts-arkui-renderfit-e.md)&gt; | Yes | Sets how the final state of the component's content is rendered during its width and height animation process.<br>If **fitMode** is set to **undefined**, the default value is used, which is equivalent to **RenderFit.TOP_LEFT**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## renderGroup

```TypeScript
renderGroup(value: boolean): T
```

Sets whether to form a render group. A render group means that the subtree composed of the current component and its child components is first rendered on an offscreen canvas and then composited with the parent component. Setting a render group allows the system to cache the rendering result, improving performance. However, if components within the render group are frequently updated, cache invalidation may lead to performance degradation. Additionally, when a render group is set and the current component's opacity is not **1**, the rendering effect may differ.

If this attribute is not set, no render group is formed by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the current component and its child components form a render group.<br> **false**: no. Rendering is performed directly without offscreen rendering.<br> **true**: yes. The current component and its child components are rendered offscreen first and then composited with the parent component. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="rendergroup-1"></a>

## renderGroup

```TypeScript
renderGroup(isGroup: Optional<boolean>): T
```

Composite the contents of this view and its children into an offscreen cache before display in the screen.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isGroup | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | if this view and its children need to composite into an offscreen cache. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## responseRegion

```TypeScript
responseRegion(value: Array<Rectangle> | Rectangle): T
```

Sets one or more touch targets.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[Rectangle](arkts-arkui-common-comp-rectangle-i.md)&gt; &#124; [Rectangle](arkts-arkui-common-comp-rectangle-i.md) | Yes | Touch target, including the position and size.<br>The default touch target is the entire component. Default value:<br>{<br>x: 0,<br>y: 0,<br>width: '100%',<br>height: '100%'<br>}<br> |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## responseRegionList

```TypeScript
responseRegionList(regions: Array<ResponseRegion>): T
```

Sets the touch target list for the component. When this API is called, the [responseRegion](#responseregion) and [mouseResponseRegion](#mouseresponseregion) APIs do not take effect.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| regions | Array&lt;[ResponseRegion](arkts-arkui-common-comp-responseregion-i.md)&gt; | Yes | Array of touch targets for the component.<br>Each touch target contains the input tool type, position, and size.<br>Default value:<br> [{<br>tool: ResponseRegionSupportedTool.ALL,<br>x: LengthMetrics.vp(0),<br>y: LengthMetrics.vp(0), <br>width: LengthMetrics.percent(1),<br>height: LengthMetrics.percent(1)<br>}] |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## restoreId

```TypeScript
restoreId(value: number): T
```

id for distribute identification.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## reuse

```TypeScript
reuse(options: ReuseOptions): T
```

Reuse id is used for identify the reuse type of each @ComponentV2 custom component, which can give user control of sub-component recycle and reuse.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ReuseOptions](arkts-arkui-common-comp-reuseoptions-i.md) | Yes | The configuration parameter for reusable custom component. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## reuseId

```TypeScript
reuseId(id: string): T
```

Reuse id is used for identify the reuse type for each custom node.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The id for reusable custom node. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## rotate

```TypeScript
rotate(value: RotateOptions): T
```

Rotates the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RotateOptions](arkts-arkui-common-comp-rotateoptions-i.md) | Yes | How the component is rotated within the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system), which takes the upper-left corner of the component as the origin (as shown in the figure below). (x, y, z) specifies a vector as the axis of rotation.<br>The axis and center of rotation are set based on the coordinate system, which remains where it is when the component is moved.<br>Default value: When **x**, **y**, and **z** are not specified, their default values are **0**, **0**, and **1**, respectively. If any of **x**, **y**, and **z** is specified, the default value for the unspecified one is **0**.<br>{<br>centerX: '50%',<br>centerY: '50%',<br> centerZ: 0,<br>perspective: 0<br>}<br>Unit: vp<br>! [coordinates](../../../reference/apis-arkui/arkui-ts/figures/coordinates.png) |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="rotate-1"></a>

## rotate

```TypeScript
rotate(options: Optional<RotateOptions>): T
```

Rotates the component. Compared with [rotate](#rotate), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[RotateOptions](arkts-arkui-common-comp-rotateoptions-i.md)&gt; | Yes | How the component is rotated within the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system), which takes the upper-left corner of the component as the origin (as shown in the figure below). (x, y, z) specifies a vector as the axis of rotation.<br>The axis and center of rotation are set based on the coordinate system, which remains where it is when the component is moved.<br>Default value: When **x**, **y**, and **z** are not specified, their default values are **0**, **0**, and **1**, respectively. If any of **x**, **y**, and **z** is specified, the default value for the unspecified one is **0**.<br>{<br>centerX: '50%',<br>centerY: '50%',<br> centerZ: 0,<br>perspective: 0<br>}<br>Unit: vp<br>! [coordinates](../../../reference/apis-arkui/arkui-ts/figures/coordinates.png)<br>If **options** is **undefined**, the component reverts to its original state with no rotation. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="rotate-2"></a>

## rotate

```TypeScript
rotate(options: Optional<RotateOptions | RotateAngleOptions>): T
```

Sets the component rotation effect. Compared with [rotate](#rotate-1), this API supports the **RotateAngleOptions** type for the **options** parameter.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[RotateOptions](arkts-arkui-common-comp-rotateoptions-i.md) &#124; [RotateAngleOptions](arkts-arkui-common-comp-rotateangleoptions-i.md)&gt; | Yes | **RotateOptions**: How the component rotates in the coordinate system (as shown below) with the upper left corner of the component as the coordinate origin. (x, y, z) specifies a vector as the axis of rotation.<br>The rotation axis and center point are defined based on the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system). When the component moves, the coordinate system does not follow it.<br>Default value: When **x**, **y**, and **z** are not specified, their default values are **0**, **0**, and **1**, respectively. If any of **x**, **y**, and **z** is specified, the default value for the unspecified one is **0**.<br>{<br>centerX: '50%',<br>centerY: '50%',<br>centerZ: 0,<br>perspective: 0<br>}<br>**RotateAngleOptions**: How the component rotates in thecoordinate system (as shown below) with the upper left corner of the component as the coordinate origin. angleX, angleY, angleZ specifies the rotation angle on the three axes.<br>Default value:<br>{<br>angleX:0,<br>angleY: 0,<br>angleZ:0,<br>centerX: '50%',<br>centerY: '50%',<br>centerZ: 0,<br>perspective: 0<br>}<br>! [coordinates](../../../reference/apis-arkui/arkui-ts/figures/coordinates.png)<br>If **options** is **undefined**, the component reverts to its original state with no rotation. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## safeAreaPadding

```TypeScript
safeAreaPadding(paddingValue: Padding | LengthMetrics | LocalizedPadding): T
```

Sets the safe area padding attribute. It allows a container to add a component-level safe area to itself for child components to extend into, and supports the [attributeModifier](#attributemodifier) method for dynamically setting attributes. Unlike padding, **safeAreaPadding** is used to set a component-level safe area for child components to extend into, while **padding** is used to set the inner padding of the component content area. The two can be set at the same time and take effect separately.

> **NOTE:** 
> 
> This API can be called within
> [attributeModifier](#attributemodifier) since API version 18.
> 
> When parent and ancestor containers define component-level safe areas, child components can detect and
> utilize these areas, referred to as Accumulated Safe Area Expansion (SAE), which represents the maximum
> extendable length in each direction. When ancestor containers have contiguous **safeAreaPadding**
> (undivided by margin, border, or padding), SAE accumulates recursively outward until no adjacent outer
> **safeAreaPadding** exists or the recursion extends beyond the page container. System-level avoid areas
> (status bar, navigation bar, notch areas, and more) are treated as the page container's inherent
> **safeAreaPadding** and participate in SAE calculations. For details about the avoid areas, see
> [Safe Area](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-expand-safe-area.md).
> These component-level safe areas can be leveraged by combining with other attributes. For example,
> setting the
> [ignoreLayoutSafeArea]
> (../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-expand-safe-area.md#ignorelayoutsafearea20)
> attribute on a child component allows it to extend its layout into the SAE region.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**Widget capability:** This API can be used in ArkTS widgets since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| paddingValue | Padding &#124; LengthMetrics &#124; [LocalizedPadding](../arkts-apis/arkts-arkui-localizedpadding-i.md) | Yes | Safe area padding of the component, which is used to create a component-level safe area inside the component for child components to extend into.<br>Default value: **0** <br>Unit: vp<br>When **paddingValue** is set to a percentage, the top, bottom, left, and right padding all use the width of the parent container as the base value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## saturate

```TypeScript
saturate(value: number): T
```

Applies a saturation effect to the component. If this API is not used, there will be no change by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Saturation of the component. The saturation is the ratio of the chromatic component to the achromatic component (gray) in a color. If the value is **1**, the original image is displayed. If the value is greater than **1**, a higher percentage of the chromatic component indicates a higher saturation. If the value is less than **1**, a higher percentage of the achromatic component indicates a lower saturation.<br> Recommended value range: [0, 50)<br>**NOTE:** <br>A value less than 0 evaluates to the value **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="saturate-1"></a>

## saturate

```TypeScript
saturate(saturate: Optional<number>): T
```

Applies a saturation effect to the component. If this API is not used, there will be no change by default. Compared to [saturate](#saturate), the **saturate** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| saturate | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Saturation of the component. The saturation is the ratio of the chromatic component to the achromatic component (gray) in a color. If the value is **1**, the original image is displayed. If the value is greater than **1**, a higher percentage of the chromatic component indicates a higher saturation. If the value is less than **1**, a higher percentage of the achromatic component indicates a lower saturation.<br>Recommended value range: [0, 50)<br>**NOTE:** <br>A value less than 0 evaluates to the value **0**.<br>If **saturate** is **undefined**, the saturation effect is reset to **1.0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## scale

```TypeScript
scale(value: ScaleOptions): T
```

Scales the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScaleOptions](arkts-arkui-common-comp-scaleoptions-i.md) | Yes | Scale ratio along the x-, y-, and z-axis. The default value is **1**. **centerX** and **centerY** are used to set the scale center point.<br>Default value:<br>{<br>x: 1,<br>y: 1,<br>z: 1,<br> centerX:'50%',<br>centerY:'50%'<br>} |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="scale-1"></a>

## scale

```TypeScript
scale(options: Optional<ScaleOptions>): T
```

Scales the component. Compared with [scale](#scale), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ScaleOptions](arkts-arkui-common-comp-scaleoptions-i.md)&gt; | Yes | Scale ratio along the x-, y-, and z-axis. The default value is **1**. **centerX** and **centerY** are used to set the scale center point.<br>Default value:<br>{<br>x: 1,<br>y: 1,<br>z: 1,<br>centerX:'50%',<br>centerY:'50%'<br>}<br>If **options** is **undefined**, the component reverts to its original state with no scaling. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## sepia

```TypeScript
sepia(value: number): T
```

Converts the image to a sepia tone, reducing color intensity to create a warm, vintage image style.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Intensity of the sepia filter. A value of 1 results in a completely sepia image, values less than or equal to 0 leave the image unchanged, and values greater than 1 increase the color shift, making the image brighter and more yellow or red, though this is not a standard sepia effect.<br>Value range: [0, +∞). Recommended value range: (0, 1]. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="sepia-1"></a>

## sepia

```TypeScript
sepia(sepia: Optional<number>): T
```

Converts the image to a sepia tone, reducing color intensity to create a warm, vintage image style. Compared to [sepia](#sepia), this API supports the **undefined** type for the **sepia** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sepia | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Intensity of the sepia filter. A value of 1 results in a completely sepia image, values less than or equal to 0 leave the image unchanged, and values greater than 1 increase the color shift, making the image brighter and more yellow or red, though this is not a standard sepia effect.<br>If **sepia** is **undefined**, the component reverts to its original effect.<br> Value range: [0, +∞). Recommended value range: (0, 1]. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## shadow

```TypeScript
shadow(value: ShadowOptions | ShadowStyle): T
```

Applies a shadow effect to the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md) | Yes | Shadow of the component.<br>When the value type is **ShadowOptions**, the blur radius, shadow color, and offset along the x-axis and y-axis can be specified.<br> When the value type is **ShadowStyle**, the shadow style can be specified.<br>**Since:** 10 |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="shadow-1"></a>

## shadow

```TypeScript
shadow(options: Optional<ShadowOptions | ShadowStyle>): T
```

Applies a shadow effect to the component. Compared to [shadow](#shadow), the **options** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md) &#124; [ShadowStyle](arkts-arkui-common-comp-shadowstyle-e.md)&gt; | Yes | Shadow of the component.<br>When the value type is **ShadowOptions**, the blur radius, shadow color, and offset along the x-axis and y-axis can be specified.<br> When the value type is **ShadowStyle**, the shadow style can be specified.<br>If **options** is **undefined**, the component reverts to its original effect with no shadow. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## sharedTransition

```TypeScript
sharedTransition(id: string, options?: sharedTransitionOptions): T
```

Sets the shared transition animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Transition of the shared element. If the same **id** value is configured for a component on the two pages, this component is considered as a shared element of the pages. If the **id** value is an empty string, no transition will be applied to the component. |
| options | [sharedTransitionOptions](arkts-arkui-common-comp-sharedtransitionoptions-i.md) | No | Parameters of the shared element transition animation. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## shouldBuiltInRecognizerParallelWith

```TypeScript
shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback): T
```

Provides a callback to set the parallel relationship between built-in gestures and gestures of other components in the response chain. The corresponding C API is [setInnerGestureParallelTo](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setinnergestureparallelto).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ShouldBuiltInRecognizerParallelWithCallback](arkts-arkui-common-comp-shouldbuiltinrecognizerparallelwithcallback-t.md) | Yes | A callback instance used when a component is doing touch test. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## shouldRecognizerParallelWith

```TypeScript
shouldRecognizerParallelWith(callback: ShouldRecognizerParallelWithCallback): T
```

Provides a callback to set the parallel relationship between gestures of the current component and gestures of other components in the response chain. This callback uses an asynchronous callback. The corresponding C API is [setGestureParallelTo](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ShouldRecognizerParallelWithCallback](arkts-arkui-common-comp-shouldrecognizerparallelwithcallback-t.md) | Yes | A callback instance used when a component is doing touch test. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## size

```TypeScript
size(value: SizeOptions): T
```

Sets the width and height of the component itself. After the setting, the layout and display size of the component in the parent container are affected. <br>Since API version 10, this API supports the calc calculation feature.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SizeOptions](../arkts-apis/arkts-arkui-sizeoptions-i.md) | Yes | Width and height.<br>Abnormal value: If the parameter is **undefined**, the attribute setting does not take effect. For other abnormal values, the **size** attribute is restored to the default behavior when it is not configured.<br>Unit: vp |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## smartGestureShortcut

```TypeScript
smartGestureShortcut(options?: SmartGestureShortcutOptions): T
```

Enable or disable specific smart gesture shortcuts, and set response priorities for them.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SmartGestureShortcutOptions](arkts-arkui-common-comp-smartgestureshortcutoptions-i.md) | No | Options for configuring smart gesture shortcuts. In SmartGestureShortcutOptions: enabled is used to configure whether the component responds to smart gestures. selectable is used to set whether the component displays and retains a selected state after being selected by a smart gesture operation. action is used to set the smart gesture response priority. Currently, only GestureShortcut.PRIMARY is supported, which makes the component the primary response target for smart gesture operations such as swiping and tapping. It is recommended to explicitly pass these parameters to avoid inconsistencies caused by default configurations. For default configuration handling, please refer to [SmartGestureShortcutOptions](arkts-arkui-common-comp-smartgestureshortcutoptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | return component instance who call the method. |

## sphericalEffect

```TypeScript
sphericalEffect(value: number): T
```

Applies a spherical effect to the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Spherical degree of the component.<br>The value ranges from 0 to 1.<br>**NOTE:** <br>1. If the value is **0**, the component remains unchanged. If the value is 1, the component is completely spherical. Between **0** and **1**, a larger value indicates a higher spherical degree.<br>A value less than 0 is handled as the value **0**. A value greater than 1 is handled as the value **1**.<br>2. The component's shadow and outer stroke do not support spherical effects.<br>3. If the value is greater than 0, the component is frozen, and its content is drawn to the transparent offscreen buffer. To update the component attributes, set the value to **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="sphericaleffect-1"></a>

## sphericalEffect

```TypeScript
sphericalEffect(effect: Optional<number>): T
```

Applies a spherical effect to the component. Compared to [sphericalEffect&lt;sup&gt;12+&lt;/sup&gt;](#sphericaleffect), the **effect** parameter supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Spherical degree of the component.<br>The value ranges from 0 to 1.<br> **NOTE:** <br>1. If the value is **0**, the component remains unchanged. If the value is 1, the component is completely spherical. Between **0** and **1**, a larger value indicates a higher spherical degree.<br>A value less than 0 is handled as the value **0**. A value greater than 1 is handled as the value **1**.<br>2. The component's shadow and outer stroke do not support spherical effects.<br>3. If **effect** is set to a positive number, the component is frozen, and its content is drawn to the transparent offscreen buffer. To update the component attributes, set **effect** to **0**.<br>If **effect** is **undefined**, the spherical degree reverts to **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## stateStyles

```TypeScript
stateStyles(value: StateStyles): T
```

Sets the state-specific styles for the component.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](#attributemodifier).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [StateStyles](arkts-arkui-common-comp-statestyles-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## sweepGradient

```TypeScript
sweepGradient(value: SweepGradientOptions): T
```

Angle Gradient center:is the center point of the angle gradient start:Start point of angle gradient. The default value is 0 end:End point of angle gradient. The default value is 0 rotating:rotating. The default value is 0 colors:Color description for gradients repeating:repeating. The default value is false

Anonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SweepGradientOptions](arkts-arkui-common-comp-sweepgradientoptions-i.md) | Yes | <br>**Since:** 18 |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

<a id="sweepgradient-1"></a>

## sweepGradient

```TypeScript
sweepGradient(options: Optional<SweepGradientOptions>): T
```

Angle Gradient center:is the center point of the angle gradient start:Start point of angle gradient. The default value is 0 end:End point of angle gradient. The default value is 0 rotating:rotating. The default value is 0 colors:Color description for gradients repeating:repeating. The default value is false

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SweepGradientOptions](arkts-arkui-common-comp-sweepgradientoptions-i.md)&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## systemBarEffect

```TypeScript
systemBarEffect(): T
```

Applies a system bar effect to the component, which means to invert colors based on the background and add a blur.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| T | return the component attribute. |

## systemMaterial

```TypeScript
systemMaterial(material: SystemUiMaterial | undefined): T
```

Sets the system material for a component. Different system materials have different attribute effects. This API affects the background color ([backgroundColor](#backgroundcolor)), border color ([borderColor](#bordercolor)), border width ([borderWidth](#borderwidth)), and shadow ([shadow](#shadow)). You are advised not to use this API together with the aforementioned APIs. For details about the example, see [Setting the System Material](../../../reference/apis-arkui/arkts-apis-uimaterial-sys.md#example-1-setting-the-system-material).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| material | [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md) &#124; undefined | Yes | System material object of the component. Setting it to **undefined** will make the component return to the no-material effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## tabIndex

```TypeScript
tabIndex(index: number): T
```

Sets the tab navigation order of the component in sequential focus navigation with the **Tab** key. Components without explicit **tabIndex** settings follow default focus navigation rules.

> **NOTE:** 
> 
> - **tabIndex** only customizes **Tab** key navigation. For arrow key navigation customization, use [nextFocus](#nextfocus).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Tab navigation order of the component in sequential focus navigation with the **Tab** key. When components with positive **tabIndex** values are present, only these components are reachable through sequential focus navigation, and they are navigated cyclically in ascending order based on the **tabIndex** value. When components with positive **tabIndex** values are not present, those components with a **tabIndex** value of **0** are navigated based on the preset focus navigation rule.<br>The [UiExtension](../arkts-apis/arkts-arkui-arkui-uiextension.md) component does not support **tabIndex**. As such, using **tabIndex** on [hierarchical pages](../../../ui/arkts-common-events-focus-event.md#basic-concepts) that contain **UiExtension** components may lead to disordered focus navigation.<br>- **tabIndex** &gt;= 0: The component is focusable and can be reached through sequential keyboard navigation.<br>- **tabIndex** &lt; 0 (usually **tabIndex** = -1): The component is focusable, but cannot be reached through sequential keyboard navigation.<br> **NOTE:** <br> **tabIndex** and **focusScopeId** cannot be used together. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## tabStop

```TypeScript
tabStop(isTabStop: boolean): T
```

Set TabStop on component focus

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isTabStop | boolean | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## toolbar

```TypeScript
toolbar(value: CustomBuilder): T
```

Config toolbar for current component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## touchable

```TypeScript
touchable(value: boolean): T
```

Whether the component can respond to finger interactions such as click and touch events.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [hitTestBehavior](#hittestbehavior)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the component can respond to finger interactions such as click and touch events.<br>**true** (default): The component can respond to finger interactions. **false**: The component cannot respond to finger interactions. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## transform

```TypeScript
transform(value: object): T
```

Displays the matrix transformation when 2D transformation is performed. If 3D transformation is included, the [transform3D](#transform3d) API is required.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | object | Yes | Transformation matrix of the component. Only the [Matrix4Transit](../arkts-apis/arkts-arkui-matrix4.md) object type is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="transform-1"></a>

## transform

```TypeScript
transform(transform: Optional<object>): T
```

Displays the matrix transformation when 2D transformation is performed. If 3D transformation is included, the [transform3D](#transform3d) API is required. Compared with [transform](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#transform), the transform&lt;sup&gt;18+&lt;/sup&gt; parameter supports the undefined type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;object&gt; | Yes | Transformation matrix of the component. Only the [Matrix4Transit](../arkts-apis/arkts-arkui-matrix4.md) object type is supported.<br>If **transform** is **undefined**, the component reverts to the identity matrix (no transformation). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## transform3D

```TypeScript
transform3D(transform: Optional<Matrix4Transit>): T
```

Sets the 3D transformation matrix of the component. When 3D transformation with the perspective effect is involved, the display effect of the transform interface may be incorrect. In this case, the transform3D interface is recommended.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Matrix4Transit](arkts-arkui-common-comp-matrix4transit-t.md)&gt; | Yes | 3D transformation matrix.<br>If **transform** is **undefined**, the component reverts to the identity matrix (no transformation). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## transition

```TypeScript
transition(value: TransitionOptions | TransitionEffect): T
```

Sets the transition effects used when a component is inserted or removed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TransitionOptions](arkts-arkui-common-comp-transitionoptions-i.md) &#124; [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Yes | Transition effects used when a component is inserted or removed.<br>**NOTE:** <br>For details, see [TransitionOptions](arkts-arkui-common-comp-transitionoptions-i.md) and [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="transition-1"></a>

## transition

```TypeScript
transition(effect: TransitionEffect, onFinish: Optional<TransitionFinishCallback>): T
```

Sets the transition effects used when a component is inserted or removed. Compared with [transition](#transition), this API provides the callback when the transition animation ends.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Yes | Transition effects used when a component is inserted or removed. |
| onFinish | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TransitionFinishCallback](arkts-arkui-common-comp-transitionfinishcallback-t.md)&gt; | Yes | Callback when the transition animation ends. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## translate

```TypeScript
translate(value: TranslateOptions): T
```

Translates the component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | Yes | How the component is translated within the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system), which takes the upper-left corner of the component as the origin (as shown in the figure below). Values of **x**, **y**, and **z** indicate the translation distance along the respective axis. A positive value indicates a forward movement towards the respective axis, and a negative value indicates a backward movement towards the respective axis. The translation distance can be a number or a string (for example, **'10px'** or **'10%'**).<br>Default value:<br>{<br>x: 0,<br>y: 0,<br>z: 0<br>}<br>Unit: vp<br>! [coordinates](../../../reference/apis-arkui/arkui-ts/figures/coordinates.png)<br>**NOTE:** <br>When the component is translated along the z-axis, the position of the observation point remains unchanged. As such, the component appears larger when the value of **z** places it closer to the observation point and smaller when the value of **z** places it further away from the observation point.<br>! [coordinateNode](../../../reference/apis-arkui/arkui-ts/figures/coordinateNote.png) |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="translate-1"></a>

## translate

```TypeScript
translate(translate: Optional<TranslateOptions>): T
```

Translates the component. Compared with [translate](#translate), this API supports the **undefined** type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| translate | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md)&gt; | Yes | How the component is translated within the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system), which takes the upper-left corner of the component as the origin (as shown in the figure below). Values of **x**, **y**, and **z** indicate the translation distance along the respective axis. A positive value indicates a forward movement towards the respective axis, and a negative value indicates a backward movement towards the respective axis. The translation distance can be a number or a string (for example, **'10px'** or **'10%'**).<br>Default value:<br>{<br>x: 0,<br>y: 0,<br>z: 0<br>}<br>Unit: vp<br>! [coordinates](../../../reference/apis-arkui/arkui-ts/figures/coordinates.png)<br>**NOTE:** <br>When the component is translated along the z-axis, the position of the observation point remains unchanged. As such, the component appears larger when the value of **z** places it closer to the observation point and smaller when the value of **z** places it further away from the observation point.<br>! [coordinateNode](../../../reference/apis-arkui/arkui-ts/figures/coordinateNote.png)<br>If **translate** is **undefined**, the component reverts to its original state with no translation. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## useEffect

```TypeScript
useEffect(useEffect: boolean, effectType: EffectType): T
```

Sets whether the component should apply the effects template defined by the parent effectComponent or window. If multiple parent effectComponents are found, the nearest one will be used. If no parent effectComponent is found, this method has no effect.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| useEffect | boolean | Yes | true means the component should apply the effects template defined by the parent effectComponent or window. |
| effectType | [EffectType](arkts-arkui-common-comp-effecttype-e.md) | Yes | the effect type of the effects template, defined by the parent effectComponent or window. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return the component attribute. |

<a id="useeffect-1"></a>

## useEffect

```TypeScript
useEffect(useEffect: Optional<boolean>, effectType?: EffectType): T
```

Sets whether the component should apply the effects template defined by the parent effectComponent or window. If multiple parent effectComponents are found, the nearest one will be used. If no parent effectComponent is found, this method has no effect.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| useEffect | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | true means the component should apply the effects template defined by the parent effectComponent or window. |
| effectType | [EffectType](arkts-arkui-common-comp-effecttype-e.md) | No | the effect type of the effects template, defined by the parent effectComponent or window. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return the component attribute. |

<a id="useeffect-2"></a>

## useEffect

```TypeScript
useEffect(value: boolean): T
```

Sets whether the component should apply the effects template defined by the parent effectComponent. If multiple parent effectComponents are found, the nearest one will be used. If no parent effectComponent is found, this method has no effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | true means the component should apply the effects template. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return the component attribute. |

## useShadowBatching

```TypeScript
useShadowBatching(value: boolean): T
```

Sets whether to render child node shadows at the same layer, enabling shadow overlap within the same layer.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to render child node shadows at the same layer.<br>Default value: **false**<br> **true**: Child node shadows are rendered at the same layer without overlapping.<br> **false**: Child node shadows are rendered separately, with later shadows overlapping earlier ones.<br>**NOTE:** <br>1. This feature is disabled by default. When child nodes have large shadow radius and overlapping areas, later-rendered shadows cover earlier ones. Enabling this feature renders all child shadows simultaneously without overlap.<br>2. Avoid nesting **useShadowBatching**. When used in nested mode, **useShadowBatching** takes effect for the current child node only and cannot be recursively used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="useshadowbatching-1"></a>

## useShadowBatching

```TypeScript
useShadowBatching(use: Optional<boolean>): T
```

Sets whether to render child node shadows at the same layer, enabling shadow overlap within the same layer. Compared with [useShadowBatching&lt;sup&gt;11+&lt;/sup&gt;](#useshadowbatching), this API supports the **undefined** type for the **use** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| use | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to render child node shadows at the same layer.<br>Default value: **false**<br> **true**: Child node shadows are rendered at the same layer without overlapping.<br> **false**: Child node shadows are rendered separately, with later shadows overlapping earlier ones.<br>**NOTE:** <br>1. This feature is disabled by default. When child nodes have large shadow radius and overlapping areas, later-rendered shadows cover earlier ones. Enabling this feature renders all child shadows simultaneously without overlap.<br> 2. Avoid nesting **useShadowBatching**. When used in nested mode, **useShadowBatching** takes effect for the current child node only and cannot be recursively used.<br>If **use** is **undefined**, the component reverts to its original effect of not using shadow overlapping. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## useSizeType

```TypeScript
useSizeType(value: {
    xs?: number | { span: number; offset: number };
    sm?: number | { span: number; offset: number };
    md?: number | { span: number; offset: number };
    lg?: number | { span: number; offset: number };
  }): T
```

Sets the number of occupied columns and offset columns for a specific device width type.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColColumnOption and grid_row/GridRowColumnOption

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | {     xs?: number &#124; { span: number; offset: number };     sm?: number &#124; { span: number; offset: number };     md?: number &#124; { span: number; offset: number };     lg?: number &#124; { span: number; offset: number };   } | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## visibility

```TypeScript
visibility(value: Visibility): T
```

Sets the visibility of the component. If **visibility** is not set, the component is displayed by default.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Visibility](../arkts-apis/arkts-arkui-visibility-e.md) | Yes | Whether the component is visible. When appropriate, consider using [conditional rendering](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) as a substitute. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## visualEffect

```TypeScript
visualEffect(effect: VisualEffect): T
```

Sets a visual effect that is not a filter effect.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [VisualEffect](arkts-arkui-common-comp-visualeffect-t.md) | Yes | Visual effect. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## width

```TypeScript
width(value: Length): T
```

Sets the width of the component itself. By default, the width required for the content of the child component is used. If the width of a child component is greater than that of its parent component, the child component overflows and is displayed outside the parent component. <br>Since API version 10, this API supports the calc calculation feature.

> **NOTE:** 
> 
> - In the [TextInput](./ts-basic-components-textinput.md) component, setting width to **auto** means adapting to the text width.
> 
> - In the [AlphabetIndexer](./ts-container-alphabet-indexer.md) component, setting **width** to
> **auto** means adapting to the width of the largest index item.
> 
> - In the Row, Column, and RelativeContainercomponents, setting width to auto means adapting to the child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the component to set.<br>Unit: vp<br>When a percentage is set, the width of the parent container is used as the base value.<br>Exception values: when the parameter is **undefined**, the attribute setting does not take effect; for other exception values, the width attribute is restored to the default behavior when it is not configured. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

<a id="width-1"></a>

## width

```TypeScript
width(widthValue: Length | LayoutPolicy): T
```

Sets the width of the component itself or its horizontal layout policy. By default, the width required for the content of the child component is used. If the width of a child component is greater than that of its parent component, the child component overflows and is displayed outside the parent component. <br>Since API version 15, when the parameter is of the **Length** type, this API supports the **calc** calculation feature.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| widthValue | [Length](../arkts-apis/arkts-arkui-length-t.md) &#124; [LayoutPolicy](arkts-arkui-common-comp-layoutpolicy-c.md) | Yes | Width or horizontal layout policy of the component to set.<br>Unit: vp<br>When a percentage is set, the width of the parent container is used as the base value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## zIndex

```TypeScript
zIndex(value: number): T
```

Sets the stacking order of the component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Stacking order of the component relative to its sibling components in a container. The components with a larger **zIndex** value cover those with a smaller one. When dynamically changing zIndex does not involve adding or removing sibling nodes, the components are sorted stably based on their previous stack level. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
