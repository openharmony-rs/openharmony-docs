# LoadingProgress properties/events

```TypeScript
declare class LoadingProgressAttribute extends CommonMethod<LoadingProgressAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

> **NOTE:** 
> 
> The component should be set to a reasonable width and height. When the width and height of the component are set
> too large, the loading progress animation may not meet the expected effect.

**Inheritance/Implementation:** LoadingProgressAttribute extends CommonMethod&lt;LoadingProgressAttribute&gt;

**Since:** 8

<!--Device-unnamed-declare class LoadingProgressAttribute extends CommonMethod<LoadingProgressAttribute>--><!--Device-unnamed-declare class LoadingProgressAttribute extends CommonMethod<LoadingProgressAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor)
```

Sets the foreground color for the **LoadingProgress** component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-LoadingProgressAttribute-color(value: ResourceColor): LoadingProgressAttribute--><!--Device-LoadingProgressAttribute-color(value: ResourceColor): LoadingProgressAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Foreground color of the loading progress bar.<br>Default value: <br>API version 10 and earlier: '#99666666'<br>API version 11 and later: '#ff666666' |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<LoadingProgressConfiguration>)
```

Creates a content modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LoadingProgressAttribute-contentModifier(modifier: ContentModifier<LoadingProgressConfiguration>): LoadingProgressAttribute--><!--Device-LoadingProgressAttribute-contentModifier(modifier: ContentModifier<LoadingProgressConfiguration>): LoadingProgressAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[LoadingProgressConfiguration](arkts-arkui-loadingprogress-comp-loadingprogressconfiguration-i.md)&gt; | Yes | Method for customizing the content area on the LoadingProgress component.<br>modifier: content modifier. Developers need to customize a class to implement the ContentModifier interface. |

## enableLoading

```TypeScript
enableLoading(value: boolean)
```

Sets whether to display the LoadingProgress animation. The component still takes up space in the layout when the loading animation is not shown. The universal attribute Visibility.Hidden hides the entire component area, including the regions specified by [border](arkts-arkui-common-comp-commonmethod-c.md#border) and [padding](arkts-arkui-common-comp-commonmethod-c.md#padding). In contrast, when the value of **enableLoading** is set to **false**, only the loading animation itself is hidden without affecting the borders or other elements.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LoadingProgressAttribute-enableLoading(value: boolean): LoadingProgressAttribute--><!--Device-LoadingProgressAttribute-enableLoading(value: boolean): LoadingProgressAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to display the LoadingProgress animation.<br>Default value: true, where true means to display the LoadingProgress animation and false means not to display it. |
