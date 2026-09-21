# Toggle properties/events

```TypeScript
declare class ToggleAttribute extends CommonMethod<ToggleAttribute>
```

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** ToggleAttribute extends CommonMethod<ToggleAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ToggleConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[ToggleConfiguration](arkts-arkui-toggle-comp-toggleconfiguration-i.md)&gt; | Yes | Content modifier to apply to the current component.<br> **modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

## onChange

```TypeScript
onChange(callback: (isOn: boolean) => void)
```

Triggered when the toggle status changes.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (isOn: boolean) =&gt; void | Yes |  |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

Sets the background color of the component when it is turned on.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the component when it is turned on.<br>Default value:<br>When **ToggleType** is set to **Switch**, the default value is **$r('sys.color.ohos_id_color_emphasize')**.<br>When **ToggleType** is set to **Checkbox**, the default value is **$r('sys.color.ohos_id_color_emphasize')**.<br> When **ToggleType** is set to **Button**, the default value is **$r('sys.color.ohos_id_color_emphasize')** with the opacity of **$r('sys.float.ohos_id_alpha_highlight_bg')**. |

## switchPointColor

```TypeScript
switchPointColor(color: ResourceColor)
```

Sets the color of the circular slider when the component is of the **Switch** type. This attribute is valid only when **type** is set to **ToggleType.Switch**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color of the circular slider when the component is of the **Switch** type.<br> Default value: **$r('sys.color.ohos_id_color_foreground_contrary')** |

## switchStyle

```TypeScript
switchStyle(value: SwitchStyle)
```

Sets the style for the component of the **Switch** type. This attribute is valid only when **type** is set to **ToggleType.Switch**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SwitchStyle](arkts-arkui-toggle-comp-switchstyle-i.md) | Yes | Style of the component of the **Switch** type. |
