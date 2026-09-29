# CheckboxGroup properties/events

```TypeScript
declare class CheckboxGroupAttribute extends CommonMethod<CheckboxGroupAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** CheckboxGroupAttribute extends CommonMethod<CheckboxGroupAttribute>

**Since:** 8

<!--Device-unnamed-declare class CheckboxGroupAttribute extends CommonMethod<CheckboxGroupAttribute>--><!--Device-unnamed-declare class CheckboxGroupAttribute extends CommonMethod<CheckboxGroupAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checkboxShape

```TypeScript
checkboxShape(value: CheckBoxShape)
```

Sets the check box shape of the check box group.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-CheckboxGroupAttribute-checkboxShape(value: CheckBoxShape): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-checkboxShape(value: CheckBoxShape): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CheckBoxShape](../arkts-apis/arkts-arkui-checkboxshape-e.md) | Yes | Check box shape of the **CheckboxGroup** component, including circle and rounded square.<br>Default value: **CheckBoxShape.CIRCLE** <br>**Note:** <br>The **CheckboxGroup** component is displayed in the set shape.<br>All check boxes in the **CheckboxGroup** component for which the shape type is not set separately use the same shape as the **CheckboxGroup** component.<br>For the check box in the **CheckboxGroup** component for which the shape type is set separately, its own shape setting takes precedence over that of the **CheckboxGroup** component, and it is displayed in its own shape.<br>An invalid value is handled as the default value. |

<a id="checkboxshape-1"></a>

## checkboxShape

```TypeScript
checkboxShape(shape: Optional<CheckBoxShape>)
```

Sets the check box shape of the check box group. Available options include circle and rounded square. Compared with [checkboxShape](#checkboxshape)&lt;sup&gt;12+&lt;/sup&gt;, this API supports the **undefined** type for the **shape** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-CheckboxGroupAttribute-checkboxShape(shape: Optional<CheckBoxShape>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-checkboxShape(shape: Optional<CheckBoxShape>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shape | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CheckBoxShape](../arkts-apis/arkts-arkui-checkboxshape-e.md)&gt; | Yes | Check box shape of the check box group, including circle and rounded square.<br>When the value of **shape** is **undefined**, the default value is **CheckBoxShape.CIRCLE**.<br> **Note:** <br>The **CheckboxGroup** component is displayed in the set shape.<br>All check boxes in the **CheckboxGroup** component for which the shape type is not set separately use the same shape as the **CheckboxGroup** component.<br>For the check box in the **CheckboxGroup** component for which the shape type is set separately, its own shape setting takes precedence over that of the **CheckboxGroup** component, and it is displayed in its own shape.<br>An invalid value is handled as the default value. |

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<CheckBoxGroupConfiguration>>)
```

Customize the CheckboxGroup content area. When this attribute is set, the settings of other attributes become invalid.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-CheckboxGroupAttribute-contentModifier(modifier: Optional<ContentModifier<CheckBoxGroupConfiguration>>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-contentModifier(modifier: Optional<ContentModifier<CheckBoxGroupConfiguration>>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[CheckBoxGroupConfiguration](arkts-arkui-checkboxgroup-comp-checkboxgroupconfiguration-i.md)&gt;&gt; | Yes | Content modifier to apply to the **TextTimer** component.<br>modifier: content modifier. You need to customize a class to implement the ContentModifier interface. <br>If **modifier** is set to **undefined**, no content modifier is used. |

## mark

```TypeScript
mark(value: MarkStyle)
```

Sets the check mark style of the check box.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CheckboxGroupAttribute-mark(value: MarkStyle): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-mark(value: MarkStyle): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [MarkStyle](../arkts-apis/arkts-arkui-markstyle-i.md) | Yes | Check mark style of the check box.<br>An invalid value is handled as the default value. |

<a id="mark-1"></a>

## mark

```TypeScript
mark(style: Optional<MarkStyle>)
```

Sets the check mark style of the check box. Compared with [mark](#mark)&lt;sup&gt;10+&lt;/sup&gt;, this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CheckboxGroupAttribute-mark(style: Optional<MarkStyle>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-mark(style: Optional<MarkStyle>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[MarkStyle](../arkts-apis/arkts-arkui-markstyle-i.md)&gt; | Yes | Check mark style of the check box.<br>If **style** is set to **undefined**, the previous value is retained. |

## onChange

```TypeScript
onChange(callback: OnCheckboxGroupChangeCallback)
```

Triggered when the selected status of the check box group or any check box wherein changes.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CheckboxGroupAttribute-onChange(callback: OnCheckboxGroupChangeCallback): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-onChange(callback: OnCheckboxGroupChangeCallback): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnCheckboxGroupChangeCallback](arkts-arkui-checkboxgroup-comp-oncheckboxgroupchangecallback-t.md) | Yes | Information about the check box group.<br>**Since:** 18 |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<OnCheckboxGroupChangeCallback>)
```

Triggered when the selected status of the check box group or any check box wherein changes. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-CheckboxGroupAttribute-onChange(callback: Optional<OnCheckboxGroupChangeCallback>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-onChange(callback: Optional<OnCheckboxGroupChangeCallback>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnCheckboxGroupChangeCallback](arkts-arkui-checkboxgroup-comp-oncheckboxgroupchangecallback-t.md)&gt; | Yes | Information about the check box group.<br>If **callback** is set to **undefined**, the callback function is not used. |

## selectAll

```TypeScript
selectAll(value: boolean)
```

Sets whether to select all. If the **select** attribute is set for a [Checkbox](arkts-arkui-checkbox-comp.md) component in the same group, the setting of the **Checkbox** has a higher priority.

When used with components that have caching functionality (such as [List](arkts-arkui-list-comp.md)), the selection state of uncreated check boxes must be controlled by the developer.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CheckboxGroupAttribute-selectAll(value: boolean): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-selectAll(value: boolean): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to select all.<br>Default value: **false**<br>If the value is **true**, all check boxes in the group are selected. If the value is **false**, all check boxes in the group are deselected.<br>If the [Checkbox](arkts-arkui-checkbox-comp.md) in the same group has the **select** attribute explicitly set, the **select** attribute of the **Checkbox** takes precedence. |

<a id="selectall-1"></a>

## selectAll

```TypeScript
selectAll(isAllSelected: Optional<boolean>)
```

Sets whether to select all. If the **select** attribute is set for a [Checkbox](arkts-arkui-checkbox-comp.md) component in the same group, the setting of the **Checkbox** has a higher priority. Compared with [selectAll](#selectall), this API supports the **undefined** type for the **isAllSelected** parameter.

When used with components that have caching functionality (such as [List](arkts-arkui-list-comp.md)), the selected state of uncreated check boxes must be controlled by the developer.

This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md) and [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-CheckboxGroupAttribute-selectAll(isAllSelected: Optional<boolean>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-selectAll(isAllSelected: Optional<boolean>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAllSelected | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to select all.<br>If **isAllSelected** is set to **undefined**, the default value **false** is used. <br>The value **true** means to select all check boxes in the group, and **false** means to deselect all check boxes in the group. |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Sets the color of the selected check box.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CheckboxGroupAttribute-selectedColor(value: ResourceColor): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-selectedColor(value: ResourceColor): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the selected check box.<br>Default value: **$r('sys.color.ohos_id_color_text_primary_activated')** <br>An invalid value is handled as the default value. |

<a id="selectedcolor-1"></a>

## selectedColor

```TypeScript
selectedColor(resColor: Optional<ResourceColor>)
```

Sets the color of the selected check box. Compared with [selectedColor](#selectedcolor), this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-CheckboxGroupAttribute-selectedColor(resColor: Optional<ResourceColor>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-selectedColor(resColor: Optional<ResourceColor>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Color of the selected check box.<br>If **resColor** is set to **undefined**, the default value **$r('sys.color.ohos_id_color_text_primary_activated')** is used. <br>An invalid value is handled as the default value. |

## unselectedColor

```TypeScript
unselectedColor(value: ResourceColor)
```

Sets the border color of the check box when it is not selected.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CheckboxGroupAttribute-unselectedColor(value: ResourceColor): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-unselectedColor(value: ResourceColor): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Border color of the check box when it is not selected.<br>Default value: **$r('sys.color.ohos_id_color_switch_outline_off')** |

<a id="unselectedcolor-1"></a>

## unselectedColor

```TypeScript
unselectedColor(resColor: Optional<ResourceColor>)
```

Sets the border color of the check box when it is not selected. Compared with [unselectedColor](#unselectedcolor)&lt;sup&gt;10+&lt;/sup&gt;, this API supports the **undefined** type for the **resColor** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-CheckboxGroupAttribute-unselectedColor(resColor: Optional<ResourceColor>): CheckboxGroupAttribute--><!--Device-CheckboxGroupAttribute-unselectedColor(resColor: Optional<ResourceColor>): CheckboxGroupAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resColor | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Border color of the check box when it is not selected.<br>If **resColor** is set to **undefined**, the default value **$r('sys.color.ohos_id_color_switch_outline_off')** is used. |
