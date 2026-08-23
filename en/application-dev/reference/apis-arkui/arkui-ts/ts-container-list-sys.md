# List (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @wind_-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=608175d8fd85ddfce5e6f9d9b165b9d12862adb2 translatedAt=2026-08-21T02:25:28.399Z pushedAt=2026-08-21T08:47:17.869Z -->

A list contains a series of list items of the same width. It is suitable for presenting similar data types continuously in multiple rows, such as images and text. In long list scenarios, list items can be created on demand with lazy loading to reduce the performance overhead caused by creating a large number of child components at once.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [List](ts-container-list.md).

## Attributes

### chainAnimationOptions<sup>10+</sup>

chainAnimationOptions(value: ChainAnimationOptions)

Sets the configuration parameters of the chain animation effect. After the chain animation effect is enabled for the list, the spacing between list items changes in a linked manner following the spring physics animation during scrolling or dragging.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

> **NOTE**
>
> The chain animation effect takes effect only when the list is in single-column mode and the edge effect is of the **EdgeEffect.Spring** type. After the chain animation effect is enabled, the divider of the list is not displayed. If the space parameter is not set and the chain animation effect is enabled, the spacing defaults to 20 vp. For details, see [chainAnimation](ts-container-list.md#chainanimation).

**Parameters**

| Name   | Type                                    | Mandatory  | Description                          |
| ------ | ---------------------------------------- | ---- | ---------------------------------- |
| value  | [ChainAnimationOptions](#chainanimationoptions10) | Yes   | Configuration parameters of the chained linkage animation effect, including minimum spacing, maximum spacing, conduction coefficient, effect intensity, edge effect, stiffness, and damping, used to control the chained linkage animation effect behavior of the list.|

## ChainEdgeEffect<sup>10+</sup>

Sets the edge effect of the chain animation effect, which determines how the spacing between list items changes when the list continues to be dragged after being scrolled to the edge.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     |  Value | Description                                      |
| ------- | ------ | ---------------------------------------- |
| DEFAULT | 0 | Default effect. When the list continues to be dragged after scrolling to the edge, the spacing between list items in the drag direction decreases, <br/>and the spacing between list items in the opposite direction increases. This is suitable for scenarios that require directional stretching and rebound feedback. |
| STRETCH | 1 | When the list continues to be dragged after scrolling to the edge, the spacing between all list items increases. This is suitable for scenarios that require synchronous stretching feedback of all list items.                 |

## ChainAnimationOptions<sup>10+</sup>

Defines a collection of chain animation effect attributes, used to set the maximum spacing, minimum spacing, animation intensity, conduction coefficient, edge effect, stiffness, and damping of the list. When the list requires fine-grained control over the chained linkage elastic effect, different animation feels can be achieved by adjusting the parameters in this object.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type                                      | Read-Only  | Optional| Description                                      |
| ------------ | ---------------------------------------- | ---- | -- | ---------------------------------------- |
| minSpace     | [Length](ts-types.md#length)             | No    | No | Minimum spacing of the chained linkage animation effect.<br/>Unit: same as **Length**. If the value is less than 0, 0 is used; if the value is greater than the spacing between list items (**space**), the spacing between list items is used.                            |
| maxSpace     | [Length](ts-types.md#length)             | No    | No | Maximum spacing of the chained linkage animation effect.<br/>Unit: same as **Length**. If the value is less than the spacing between list items (**space**), the spacing between list items is used.                          |
| conductivity | number                                   | No    | Yes | Conduction coefficient of the chained linkage animation effect, which controls the influence range of the linkage. The value range is [0,1]. The larger the value, the more list items are affected by the chained linkage. If the value is out of range, the default value is used.<br/>Default value: **0.7** |
| intensity    | number                                   | No    | Yes | Intensity of the chained linkage animation effect, which controls the displacement amplitude of list items in the chained linkage. The value range is [0,1]. The larger the value, the greater the displacement amplitude of list items in the chained linkage. If the value is out of range, the default value is used.<br/>Default value: **0.3** |
| edgeEffect   | [ChainEdgeEffect](#chainedgeeffect10) | No    | Yes | Edge effect of the chained linkage animation effect, which controls how the spacing changes after the list scrolls to the edge. **DEFAULT** presents directional stretching and rebound feedback, and **STRETCH** presents synchronous stretching feedback of all list items.<br/>Default value: **ChainEdgeEffect.DEFAULT** |
| stiffness    | number                                   | No    | Yes | Stiffness of the chained linkage animation effect, which controls the rebound speed and animation hardness.<br/>Value range: (0, +∞). The larger the value, the faster the rebound speed and the harder the animation; the smaller the value, the softer the animation. If the value is set to a value less than or equal to 0, the current value remains unchanged; if it has never been set, the default value is used.<br/>Default value: **228** |
| damping      | number                                   | No    | Yes | Damping of the chained linkage animation effect, which controls the oscillation decay speed.<br/>Value range: (0, +∞). The larger the value, the faster the animation decays and the fewer the oscillations; the smaller the value, the more likely the animation is to oscillate. If the value is set to a value less than or equal to 0, the current value remains unchanged; if it has never been set, the default value is used.<br/>Default value: **30** |