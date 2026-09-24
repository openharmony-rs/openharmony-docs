# Radio properties/events

```TypeScript
declare class RadioAttribute extends CommonMethod<RadioAttribute>
```

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** RadioAttribute extends CommonMethod<RadioAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked(value: boolean)
```

Sets whether the radio button is selected.

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

Since API version 18, this attribute supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the radio button is selected.<br>Default value: **false**<br>**true**: The radio button is selected. **false**: The radio button is not selected. |

<a id="checked-1"></a>

## checked

```TypeScript
checked(isChecked: Optional<boolean>)
```

Sets whether the radio button is selected. Compared with [checked](#checked), this API supports the **undefined** type for the **isChecked** parameter.

This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md) and [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isChecked | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether the radio button is selected.<br>If **isChecked** is set to **undefined**, the default value **false** is used.<br>**true**: The radio button is selected. **false**: The radio button is not selected. |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<RadioConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[RadioConfiguration](arkts-arkui-radio-comp-radioconfiguration-i.md)&gt; | Yes | Content modifier to apply to the current component.<br> **modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

<a id="contentmodifier-1"></a>

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<RadioConfiguration>>)
```

Creates a content modifier. Compared with [contentModifier](#contentmodifier)&lt;sup&gt;12+&lt;/sup &gt;, this API supports the **undefined** type for the **modifier** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[RadioConfiguration](arkts-arkui-radio-comp-radioconfiguration-i.md)&gt;&gt; | Yes | Content modifier to apply to the current component.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. <br>If **modifier** is set to **undefined**, no content modifier is used. |

## onChange

```TypeScript
onChange(callback: (isChecked: boolean) => void)
```

Triggered when the selected state of the radio button changes.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (isChecked: boolean) =&gt; void | Yes | Selected state of the radio button.<br>The value **true** means that the radio button changes from unselected to selected, and **false** means that the radio button changes from selected to unselected. |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<OnRadioChangeCallback>)
```

Triggered when the selected state of the radio button changes. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnRadioChangeCallback](arkts-arkui-radio-comp-onradiochangecallback-t.md)&gt; | Yes | Callback for radio button selection state changes.<br>If **callback** is set to **undefined**, the callback function is not used. |

## radioStyle

```TypeScript
radioStyle(value?: RadioStyle)
```

Sets the style of the radio button in selected or deselected state.

Since API version 10, this API is supported in ArkTS widgets.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RadioStyle](arkts-arkui-radio-comp-radiostyle-i.md) | No | Style of the radio button in selected or deselected state. |
