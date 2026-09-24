# LazyColumnLayout properties/events

```TypeScript
export declare class LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>
```

Defines the lazy column layout attribute.

@extends CommonMethod&lt;LazyColumnLayoutAttribute&gt;

**Inheritance/Implementation:** LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { LazyColumnLayout, LazyColumnLayoutAttribute } from '@kit.ArkUI';
```

## alignItems

```TypeScript
alignItems(value: HorizontalAlign | undefined)
```

Sets the horizontal alignment of the row content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [HorizontalAlign](../arkts-apis/arkts-arkui-horizontalalign-e.md) &#124; undefined | Yes | the horizontal alignment of the row content.<br>Default value HorizontalAlign.Center. |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined)
```

Sets the footer of the lazy column layout.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | The footer builder function<br>Passing undefined will remove the footer. |

## header

```TypeScript
header(builder: CustomBuilder | undefined)
```

Sets the header of the lazy column layout.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; undefined | Yes | The header builder function<br>Passing undefined will remove the header. |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined)
```

Triggered when the index of child components in the visible area changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](arkts-arkui-common-comp-onvisibleindexeschangecallback-t.md) &#124; undefined | Yes | callback function, triggered when the index of child components in the visible area changes.<br>Passing undefined will unregister the callback. |

## space

```TypeScript
space(space: LengthMetrics | undefined)
```

The spacing between rows.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| space | LengthMetrics &#124; undefined | Yes | the spacing between rows.<br>Default value: 0. <br>Range: [0, +∞). |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined)
```

Sets sticky style for header and footer.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sticky | [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) &#124; undefined | Yes | The sticky style for header and footer. |
