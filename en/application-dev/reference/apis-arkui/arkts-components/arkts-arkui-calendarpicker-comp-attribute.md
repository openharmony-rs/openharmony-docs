# CalendarPicker properties/events

```TypeScript
declare class CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md#common), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md#common), the following events are supported.

**Inheritance/Implementation:** CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## edgeAlign

```TypeScript
edgeAlign(alignType: CalendarAlign, offset?: Offset)
```

Sets how the picker is aligned with the entry component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignType | [CalendarAlign](arkts-arkui-calendarpicker-comp-calendaralign-e.md) | Yes | Alignment type.<br>Default value: **CalendarAlign.END**. |
| offset | Offset | No | Offset of the picker relative to the entry component after alignment based on the specified alignment type.<br>Default value: **{dx: 0, dy: 0}** |

<a id="edgealign-1"></a>

## edgeAlign

```TypeScript
edgeAlign(alignType: Optional<CalendarAlign>, offset?: Offset)
```

Sets how the picker is aligned with the entry component. Compared with [edgeAlign](#edgealign), this API supports the **undefined** type for the **alignType** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CalendarAlign](arkts-arkui-calendarpicker-comp-calendaralign-e.md)&gt; | Yes | Alignment type.<br>Default value: **CalendarAlign.END**.<br>If the value of **alignType** is **undefined**, the default value is used. |
| offset | Offset | No | Offset of the picker relative to the entry component after alignment based on the specified alignment type.<br>Default value: **{dx: 0, dy: 0}** |

## markToday

```TypeScript
markToday(enabled: boolean)
```

Whether to highlight the current system date.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to highlight the current system date.<br>- **true**: Highlight the current system date.<br>- **false**: Do not highlight the current system date.<br>Default value: **false**. |

## onChange

```TypeScript
onChange(callback: Callback<Date>)
```

Triggered when a date is selected. This event cannot be triggered by two-way bound state variables.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;Date&gt; | Yes | Selected date value.<br>**Since:** 18 |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<Callback<Date>>)
```

Triggered when a date is selected. This event cannot be triggered by two-way bound state variables. Compared with [onChange](#onchange), this API supports the **undefined** type for the **callback** parameter.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;Date&gt;&gt; | Yes | Selected date value.<br>If **callback** is set to **undefined**, the callback function is not used. |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

Sets the font color, font size, and font weight in the entry area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Font color, font size, and font weight in the entry area.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>} |

<a id="textstyle-1"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

Sets the font color, font size, and font weight in the entry area. Compared with [textStyle](#textstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Font color, font size, and font weight in the entry area.<br>Default value:<br>{<br>color: '#ff182431',<br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular<br>}<br>}<br>If the value of **style** is **undefined**, the default value is used. |
