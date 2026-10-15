# UIPickerComponent properties/events

```TypeScript
declare class UIPickerComponentAttribute extends CommonMethod<UIPickerComponentAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** UIPickerComponentAttribute extends CommonMethod&lt;UIPickerComponentAttribute&gt;

**Since:** 22

<!--Device-unnamed-declare class UIPickerComponentAttribute extends CommonMethod<UIPickerComponentAttribute>--><!--Device-unnamed-declare class UIPickerComponentAttribute extends CommonMethod<UIPickerComponentAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

Sets whether the option list can loop scrolling. When there are many options and infinite scrolling is required, enable the loop; when there are few options or the selection range needs to be limited, disable the loop.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UIPickerComponentAttribute-canLoop(isLoop: Optional<boolean>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-canLoop(isLoop: Optional<boolean>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether cyclic scrolling is supported. <br>- **true**: Cyclic scrolling is supported. <br>- **false**: Cyclic scrolling is not supported. <br>Default value: **true** <br>When the value of **isLoop** is **undefined**, the default value is used. <br>When the number of child components is less than or equal to the number of visible options (set by [displayedItemCount](#displayeditemcount), which defaults to **7**), cyclic scrolling is not performed regardless of whether **isLoop** is set to **true** or **false**. |

## displayedItemCount

```TypeScript
displayedItemCount(count: Optional<number>)
```

Sets the number of visible options in the **UIPickerComponent** container. If this API is not called, the number of visible options is 7 rows. Reduce the number of visible options when space needs to be saved, and increase it when more preview information needs to be provided. This attribute, together with [itemHeight](#itemheight), affects the display effect of the component. It is recommended to adjust it in combination with the component [height](arkts-arkui-common-comp-commonmethod-c.md#height1) attribute to ensure complete display.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-UIPickerComponentAttribute-displayedItemCount(count: Optional<int>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-displayedItemCount(count: Optional<int>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Number of visible options.<br>Value range: an integer in [2, 9]. <br>If a decimal is set, the value is rounded down to an integer. <br>If an even number is set, it is automatically converted to the odd number greater than it (for example, 2 becomes 3 and 8 becomes 9). <br>If the value is out of the range, the default value 7 rows is used. <br>If the value of **count** is **undefined**, the default value 7 rows is used. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

Sets whether to enable haptic feedback. Haptic feedback can be enabled in scenarios where the user interaction experience needs to be enhanced.

To enable haptic feedback, configure the requestPermissions field in the "module" section of the src/main/ module.json5 file of the project to request the vibration permission, as follows:

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UIPickerComponentAttribute-enableHapticFeedback(enable: Optional<boolean>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-enableHapticFeedback(enable: Optional<boolean>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable haptic feedback.<br>- **true**: enables haptic feedback. <br>- **false**: disables haptic feedback. <br>Default value: **true** <br>When the value of enable is **undefined**, the default value is used. <br>After it is enabled, whether haptic feedback is available depends on the hardware support of the system. |

## itemHeight

```TypeScript
itemHeight(height: Optional<LengthMetrics>)
```

Sets the height of each option in the **UIPickerComponent** container. If this API is not called, the height of each option is 40 vp. When the option content is large or a larger font is required, you can increase the height to avoid content clipping. When the option content is concise or a compact display is required, you can decrease the height. This attribute, together with [displayedItemCount](#displayeditemcount), affects the display effect of the component. You are advised to adjust it in combination with the component [height](arkts-arkui-common-comp-commonmethod-c.md#height1) attribute to ensure complete display.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-UIPickerComponentAttribute-itemHeight(height: Optional<LengthMetrics>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-itemHeight(height: Optional<LengthMetrics>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Height of an option. <br>Unit: same as that of [LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md). <br>Value range: [40vp, 64vp] <br>If the value is less than 40 vp or greater than 64 vp, the default value 40 vp is used. <br>If the value of height is undefined, the default value 40 vp is used. <br>The "percentage" type is not supported. |

## onChange

```TypeScript
onChange(callback: Optional<OnUIPickerComponentCallback>)
```

Triggered when the selected item changes while the picker options are being scrolled. It applies to scenarios where the UI needs to be updated in real time, corresponding data needs to be loaded, or related logic needs to be executed when the selected item changes.

> **NOTE:** 
> 
> If more than half of an option enters the selected item area, the option becomes the selected item.
> 
> The selected item area can be identified by setting
> [selectionIndicator](#selectionindicator). If the selected item indicator is set
> to the background, the background area is the selected item area. If the selected item indicator is set to a
> divider line, the area between the center lines of the upper and lower divider lines is the selected item area.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UIPickerComponentAttribute-onChange(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-onChange(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnUIPickerComponentCallback](arkts-arkui-uipickercomponent-comp-onuipickercomponentcallback-t.md)&gt; | Yes | Callback invoked when the selected item changes.<br>When the value of callback is undefined, the callback is not used. |

## onScrollStop

```TypeScript
onScrollStop(callback: Optional<OnUIPickerComponentCallback>)
```

Triggered when the picker stops scrolling. The picker stops scrolling when the scrolling animation triggered by a certain action is completely finished. If a new scrolling animation is triggered before the current scrolling animation finishes, it is not considered as scrolling stop. This event is suitable for scenarios where the final selection result needs to be submitted, the loading animation needs to be stopped, or a one-time callback needs to be executed after scrolling ends.

> **NOTE:** 
> 
> Differences between **onChange** and **onScrollStop**:
> 
> - **Trigger timing**: **onChange** is triggered immediately when the selected item changes; **onScrollStop** is triggered after the scrolling animation completely stops.
> 
> - **Trigger frequency**: During continuous scrolling, **onChange** may be triggered multiple times (each time the selected item changes); **onScrollStop** is triggered only once when scrolling stops.
> 
> - **Use scenarios**: **onChange** is suitable for scenarios that require real-time response (such as displaying the selected content in real time and updating other components in linkage); **onScrollStop** is suitable for scenarios that require final confirmation (such as submitting the final selection result and saving data).
> 
> - **Relationship between the two**: A complete scrolling operation may trigger these two events in sequence. They can be used simultaneously or selectively based on actual requirements.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UIPickerComponentAttribute-onScrollStop(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-onScrollStop(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnUIPickerComponentCallback](arkts-arkui-uipickercomponent-comp-onuipickercomponentcallback-t.md)&gt; | Yes | Callback invoked when the picker stops scrolling. When the value of callback is undefined, the callback is not used. |

## selectionIndicator

```TypeScript
selectionIndicator(style: Optional<PickerIndicatorStyle>)
```

Sets the style of the selected item indicator. Use a background indicator when the selected area needs to be highlighted, and use a divider indicator when a simple and lightweight marker is required.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UIPickerComponentAttribute-selectionIndicator(style: Optional<PickerIndicatorStyle>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-selectionIndicator(style: Optional<PickerIndicatorStyle>): UIPickerComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerIndicatorStyle](arkts-arkui-uipickercomponent-comp-pickerindicatorstyle-i.md)&gt; | Yes | Style of the selected item indicator.<br>Default value: <br>**{<br>type: PickerIndicatorType.BACKGROUND, <br>borderRadius: {<br>value:12, <br>unit:LengthUnit.vp <br>}, <br>backgroundColor: 'sys.color.comp_background_tertiary'<br>}** <br>When the value of **style** is **undefined**, the default value is used. |
