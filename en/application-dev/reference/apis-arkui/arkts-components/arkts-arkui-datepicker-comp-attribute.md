# DatePicker properties/events

```TypeScript
declare class DatePickerAttribute extends CommonMethod<DatePickerAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

@extends CommonMethod [since 8 - 10] @extends CommonMethod&lt;DatePickerAttribute&gt; [since 11]

**Inheritance/Implementation:** DatePickerAttribute extends CommonMethod<DatePickerAttribute>

**Since:** 8

<!--Device-unnamed-declare class DatePickerAttribute extends CommonMethod<DatePickerAttribute>--><!--Device-unnamed-declare class DatePickerAttribute extends CommonMethod<DatePickerAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

Sets whether to enable cyclic scrolling.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DatePickerAttribute-canLoop(isLoop: Optional<boolean>): DatePickerAttribute--><!--Device-DatePickerAttribute-canLoop(isLoop: Optional<boolean>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable cyclic scrolling. <br>- **true**: enable cyclic scrolling. The year increments/decrements in a linked manner as the month scrolls cyclically, and the month increments/decrements in a linked manner as the day scrolls cyclically. <br>- **false**: disable cyclic scrolling. The year, month, and day stop scrolling when they reach the top or bottom of their respective columns, and they remain independent of each other without linked increment/ decrement. <br>Default value: **true** <br>If the value of **isLoop** is undefined, the default value is used. <br>**Note:** <br>When [start](arkts-arkui-datepicker-comp-datepickeroptions-i.md) or [end](arkts-arkui-datepicker-comp-datepickeroptions-i.md) is set to a non-default value, **canLoop** does not take effect. This is because after a date range limit is set, cyclic scrolling may cause the date to exceed the valid range. To ensure the accuracy of date selection, the non-cyclic mode is forcibly used. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the sensitivity to the digital crown rotation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): DatePickerAttribute--><!--Device-DatePickerAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Crown response sensitivity.<br>Default value: **CrownSensitivity.MEDIUM**, indicating a moderate response speed. |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

Sets the text style for edge items (the second item above or below the selected item).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerAttribute-disappearTextStyle(value: PickerTextStyle): DatePickerAttribute--><!--Device-DatePickerAttribute-disappearTextStyle(value: PickerTextStyle): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the edge items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} |

<a id="disappeartextstyle-1"></a>

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

Sets the text style for edge items (the second item above or below the selected item). Compared to [disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): DatePickerAttribute--><!--Device-DatePickerAttribute-disappearTextStyle(style: Optional<PickerTextStyle>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the edge items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '14fp', <br>weight: FontWeight.Regular <br>} <br>} <br>If the value of **style** is **undefined**, the default value is used. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

Sets whether to enable haptic feedback.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-enableHapticFeedback(enable: Optional<boolean>): DatePickerAttribute--><!--Device-DatePickerAttribute-enableHapticFeedback(enable: Optional<boolean>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable haptic feedback.<br>- **true**: enable haptic feedback. <br>- **false**: disable haptic feedback. <br>Default value: **true** <br>After this parameter is set to **true**, whether it takes effect depends on whether the system hardware supports it. <br>If the value of **enable** is **undefined**, the default value is used. |

## lunar

```TypeScript
lunar(value: boolean)
```

Sets whether to display dates in lunar calendar format.

> **NOTE:** 
> 
> This attribute takes effect only for Simplified Chinese and Traditional Chinese. In other languages, setting this
> attribute has no effect.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerAttribute-lunar(value: boolean): DatePickerAttribute--><!--Device-DatePickerAttribute-lunar(value: boolean): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display dates in lunar calendar format.<br>- **true**: Display dates in lunar calendar format. <br>- **false**: Do not display dates in lunar calendar format. <br>Default value: **false** |

<a id="lunar-1"></a>

## lunar

```TypeScript
lunar(isLunar: Optional<boolean>)
```

Sets whether to display dates in lunar calendar format. Compared with [lunar](#lunar), the **isLunar** parameter supports the **undefined** type.

> **NOTE:** 
> 
> This attribute takes effect only for Simplified Chinese and Traditional Chinese. In other languages, setting this
> attribute has no effect.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-lunar(isLunar: Optional<boolean>): DatePickerAttribute--><!--Device-DatePickerAttribute-lunar(isLunar: Optional<boolean>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLunar | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to display dates in lunar calendar format.<br>- **true**: Display dates in lunar calendar format. <br>- **false**: Do not display dates in lunar calendar format. <br>Default value: **false** <br>If the value of **isLunar** is **undefined**, the default value is used. |

## onDateChange

```TypeScript
onDateChange(callback: Callback<Date>)
```

Triggered when the options are completely settled at the selected position after the text content of the **DatePicker** is swiped. Settling means that the scrolling animation ends and the options stop stably at the selected position. It cannot be triggered by two-way bound state variables, but can respond to the user's swipe operation.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerAttribute-onDateChange(callback: Callback<Date>): DatePickerAttribute--><!--Device-DatePickerAttribute-onDateChange(callback: Callback<Date>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;Date&gt; | Yes | Callback used to return the selected time. The year, month, and day are the selected date; the hour and minute depend on the hour and minute of the current system time; and the second is always 00. This is applicable to scenarios where the selected date needs to be obtained, the UI needs to be updated, or service logic needs to be executed after the user confirms the date selection.<br>**Since:** 18 |

<a id="ondatechange-1"></a>

## onDateChange

```TypeScript
onDateChange(callback: Optional<Callback<Date>>)
```

Triggered when the date picker snaps to the selected item. This event cannot be triggered by two-way bound state variables. Compared to [onDateChange&lt;sup&gt;10+&lt;/sup&gt;](#ondatechange), this API supports the **undefined** type for the **callback** parameter.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-onDateChange(callback: Optional<Callback<Date>>): DatePickerAttribute--><!--Device-DatePickerAttribute-onDateChange(callback: Optional<Callback<Date>>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;Date&gt;&gt; | Yes | Callback used to return the selected time. The year, month, and day are the selected date; the hour and minute depend on the hour and minute of the current system time; and the second is always 00. This is applicable to scenarios where the selected date needs to be obtained, the UI needs to be updated, or service logic needs to be executed after the user confirms the date selection.<br>If the value of **callback** is **undefined**, the callback is not used. |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

Sets the text style for the selected item.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerAttribute-selectedTextStyle(value: PickerTextStyle): DatePickerAttribute--><!--Device-DatePickerAttribute-selectedTextStyle(value: PickerTextStyle): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the selected item.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} |

<a id="selectedtextstyle-1"></a>

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

Sets the text style for the selected item. Compared to [selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): DatePickerAttribute--><!--Device-DatePickerAttribute-selectedTextStyle(style: Optional<PickerTextStyle>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the selected item.<br>Default value: <br>{<br>color: '#ff007dff', <br>font: {<br>size: '20fp', <br>weight: FontWeight.Medium <br>} <br>} <br>If the value of **style** is undefined, the default value is used. |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

Sets the text style for candidate items (the first item immediately above or below the selected item).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerAttribute-textStyle(value: PickerTextStyle): DatePickerAttribute--><!--Device-DatePickerAttribute-textStyle(value: PickerTextStyle): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | Yes | Text color, font size, and font weight of the candidate items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} |

<a id="textstyle-1"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

Sets the text style for candidate items (the first item immediately above or below the selected item). Compared to [textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle), this API supports the **undefined** type for the **style** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-DatePickerAttribute-textStyle(style: Optional<PickerTextStyle>): DatePickerAttribute--><!--Device-DatePickerAttribute-textStyle(style: Optional<PickerTextStyle>): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | Yes | Text color, font size, and font weight of the candidate items.<br>Default value: <br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>If the value of **style** is undefined, the default value is used. |

## onChange

```TypeScript
onChange(callback: (value: DatePickerResult) => void)
```

Triggered when the date picker snaps to the selected item. This event cannot be triggered by two-way bound state variables.

This API is supported since API version 8 and deprecated since API version 10. You are advised to use [onDateChange](#ondatechange) instead.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [onDateChange](#ondatechange)(callback: Callback&lt;Date&gt;)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DatePickerAttribute-onChange(callback: (value: DatePickerResult) => void): DatePickerAttribute--><!--Device-DatePickerAttribute-onChange(callback: (value: DatePickerResult) => void): DatePickerAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: DatePickerResult) =&gt; void | Yes | Callback used to return the selected time, including the year, month, and day fields. |
