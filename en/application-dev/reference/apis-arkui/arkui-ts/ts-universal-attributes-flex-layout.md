# Flex Layout
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=386d3d79d27becb231d4edf5e42d9c56a63599cb translatedAt=2026-09-01T12:31:34.809Z -->

The flex layout provides flexible component arrangement and alignment capabilities, dynamically allocating space among child components within a container so that elements automatically expand or shrink based on available space. It is suitable for responsive UI layouts, dynamic content layouts, and complex layout implementations, and it resolves issues of traditional layouts such as difficulty in adapting to multiple devices, layout misalignment caused by content changes, and complex alignment requirements that are hard to fulfill.

>  **NOTE**
> - Supported since API version 7. For newly added APIs in later versions, the earliest API version is marked with a superscript.
>
> - **flexBasis**: Sets the base size of a component, which serves as the initial reference value for layout and takes precedence over width/height.
> - **flexGrow**: Defines the expansion ratio of a component when the parent container has remaining space. The remaining space is allocated according to the flexGrow ratio of each component.
> - **flexShrink**: Defines the shrink ratio of a component when the parent container runs out of space. The excess size is distributed according to the flexShrink ratio of each component.
> - flexBasis sets the base size, flexGrow controls the expansion behavior, and flexShrink controls the shrink behavior. The three can be used individually or in combination.
> - The following four attributes take effect only when the parent component is [Flex](ts-container-flex.md), [Column](ts-container-column.md), [Row](ts-container-row.md), or [DynamicLayout](ts-container-dynamiclayout.md). When the parent component is [GridRow](ts-container-gridrow.md), setting [alignSelf](#alignself) takes effect.

## flexBasis

flexBasis(value: number | string): T

Sets the base size of a component. This attribute can be set only when the component is a child of a Flex, Column, Row, or DynamicLayout container. After it is set, the component uses this base size as its initial size in layout calculation. When the parent container is Column or Row, you must set the size along the main axis. When the main axis size (width/height/size) is not set, Column and Row still follow the default layout behavior and adapt to the child component size on the main axis, which may affect the effect of flexBasis.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                      | Mandatory| Description                                                        |
| ------ | -------------------------- | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;string | Yes   | Base size of the component on the main axis of the parent container.<br>Default value: 'auto' (indicating that the base size of the component on the main axis is the original size of the component).<br>string type: percentage strings are not allowed. Optional values: a string that can be converted to a number (for example, '10'), a string with a length unit (for example, '10px'), or 'auto'. If a string that does not meet the requirements is passed in, the default value 'auto' is used.<br>number: value range (0, +∞), in vp (virtual pixel).<br>When an invalid value is set, this attribute is processed as the default value 'auto'.<br>[constraintSize](ts-universal-attributes-size.md#constraintsize) restricts the size range of the component. When the base size set by flexBasis exceeds the restriction range of constraintSize, it is constrained by constraintSize. |

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component, used for chained calls. |

## flexGrow


flexGrow(value: number): T

Sets the proportion of the component in the remaining space of the parent container. This attribute can be set only when the component is a child of a Flex, Column, Row, or DynamicLayout container. After it is set, the component expands according to the ratio to occupy the remaining space of the parent container. When the parent container is Column or Row, you must set the size along the main axis. When the main axis size (width/height/size) is not set, Column and Row still follow the default layout behavior and adapt to the child component size on the main axis, which may affect the remaining space allocation effect of flexGrow. Setting this attribute triggers a second layout. In scenarios with strict performance requirements, use [layoutWeight](ts-universal-attributes-size.md#layoutweight) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| value  | number | Yes   | Sets the proportion of the remaining space in the parent container along the main axis (horizontal for row layout and vertical for column layout) allocated to the component where this attribute resides. The value 0 means the component does not participate in the allocation of remaining space and keeps its original size. When the value is greater than 0, the remaining space of the parent container is allocated proportionally; the larger the value, the more space is allocated.<br>Value range: [0, +∞)<br>Default value: 0<br>When the parent container is [Column](ts-container-column.md) or [Row](ts-container-row.md), you need to set the size along the main axis ([width](ts-universal-attributes-size.md#width)/[height](ts-universal-attributes-size.md#height)/[size](ts-universal-attributes-size.md#size)); otherwise, the remaining space allocation effect of flexGrow may be affected.<br>[constraintSize](ts-universal-attributes-size.md#constraintsize) restricts the size range of the component. When the component size after flexGrow expansion exceeds the maximum limit of constraintSize, it is constrained by constraintSize.<br>When an invalid value is set, this attribute takes the default value. |

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component, used for chained calls. |

## flexShrink

flexShrink(value: number): T

Sets the proportion of the shrink size allocated to the component where this attribute resides when the parent container runs out of space. This attribute can be set only when the component is a child of a Flex, Column, Row, or DynamicLayout container. When the parent container is Column or Row, the parent container must set the size along the main axis (that is, width/height/size) for flexShrink to take effect. When the main axis size (width/height/size) is not set, Column and Row still follow the default layout behavior and adapt to the child component size on the main axis, in which case flexShrink does not take effect. Setting this attribute triggers a second layout. In scenarios with strict performance requirements, use [layoutWeight](ts-universal-attributes-size.md#layoutweight) instead.

>  **NOTE**
>
>  When [getInspectorByKey](ts-universal-attributes-component-id.md#getinspectorbykey9) is used to obtain the flexShrink attribute, if the node does not have flexShrink set, 1 is returned by default (consistent with the default value of the Flex container, but different from the default value 0 of the Column and Row containers).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

<!--Table: auto; 10%; 10%; auto-->
| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| value  | number | Yes   | Sets the proportion of the compressed size allocated to the component to which this attribute belongs when the parent container space is insufficient. The value 0 indicates that the component does not participate in compression; when the value is greater than 0, compression is performed proportionally, and a larger value indicates a larger compression amount.<br>When the parent container is [Column](ts-container-column.md) or [Row](ts-container-row.md), default value: 0, value range: [0, +∞).<br>When the parent container is [Flex](ts-container-flex.md), default value: 1, value range: [0, +∞).<br>[constraintSize](ts-universal-attributes-size.md#constraintsize) restricts the size range of the component. Even if [constraintSize](ts-universal-attributes-size.md#constraintsize) is set for [Column](ts-container-column.md) and [Row](ts-container-row.md), when the main axis size ([width](ts-universal-attributes-size.md#width)/[height](ts-universal-attributes-size.md#height)/[size](ts-universal-attributes-size.md#size)) is not set in the parent container, the default layout behavior is still followed, and the component size is adapted to the children on the main axis. In this case, flexShrink does not take effect.<br>When an exception value is set, this attribute uses the default value.|

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component, used for chained calls. |

## alignSelf

alignSelf(value: ItemAlign): T

The alignment mode of the child component along the cross axis (the direction perpendicular to the main axis) of the parent container. After it is set, it overrides the alignItems setting of the parent container. This attribute is supported only by Flex, Column, Row, DynamicLayout, and GridRow containers.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                        |
| ------ | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [ItemAlign](ts-appendix-enums.md#itemalign) | Yes   | Alignment format of the child component on the cross axis of the parent container, which overrides the alignItems setting in the [Flex](ts-container-flex.md), [Column](ts-container-column.md), [Row](ts-container-row.md), [DynamicLayout](ts-container-dynamiclayout.md), and [GridRow](ts-container-gridrow.md) layout containers. Use it when a child component needs a different alignment from other child components in the parent container (typical scenarios: most child components in the parent container are center-aligned, but a specific child component needs top or bottom alignment; or a special alignment needs to be specified for a single child component).<br>[GridCol](./ts-container-gridcol.md) can bind the alignSelf attribute to change its own layout in the cross axis direction.<br>Default value: ItemAlign.Auto (indicates inheriting the alignment setting of the parent container) |

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component, used for chained calls. |

## Example

This example shows how to set up a flex layout through the **flexBasis**, **flexGrow**, **flexShrink**, and **alignSelf** attributes.

```ts
// xxx.ets
@Entry
@Component
struct FlexExample {
  build() {
    Column({ space: 5 }) {
      Text('flexBasis').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // Base size in the main axis
      // The value of flexBasis() can be 'auto' or a number, which is equivalent to .width()/.height().
      Flex() {
        Text('flexBasis(100)')
          .flexBasis(100) // The width is 100 vp.
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text(`flexBasis('auto')`)
          .flexBasis('auto') // The width is 60% of the original width.
          .width('60%')
          .height(100)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)

      Text('flexGrow').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // flexGrow() indicates the percentage of the remaining space allocated to the component.
      Flex() {
        Text('flexGrow(2)')
          .flexGrow(2) // The width allocated to the Text component is 2/3 of the remaining width of the parent container.
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text('flexGrow(1)')
          .flexGrow(1) // The width allocated to the Text component is 1/3 of the remaining width of the parent container.
          .height(100)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)

      Text('flexShrink').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // flexShrink() indicates the percentage of the shrink size allocated to the component.
      // The value is 0 for the first Text component and 1 for the other two Text components. This means that, if the components cannot be completely displayed in the parent container, the latter two are shrunk proportionally, while the former is not shrunk.
      Flex({ direction: FlexDirection.Row }) {
        Text('flexShrink(0)')
          .flexShrink(0)
          .width('50%')
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text('default flexShrink') // The default value is 1.
          .width('40%')
          .height(100)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
        Text('flexShrink(1)')
          .flexShrink(1)
          .width('40%')
          .height(100)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)

      Text('alignSelf').fontSize(9).fontColor(0xCCCCCC).width('90%')
      // The alignSelf setting overrides the alignItems setting of the parent container.
      Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
        Text('no alignSelf,height:70')
          .width('33%')
          .height(70)
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
        Text('alignSelf End')
          .alignSelf(ItemAlign.End)
          .width('33%')
          .height(70)
          .backgroundColor(0xD2B48C)
          .textAlign(TextAlign.Center)
        Text('no alignSelf,height:100%')
          .width('34%')
          .height('100%')
          .backgroundColor(0xF5DEB3)
          .textAlign(TextAlign.Center)
      }.width('90%').height(120).padding(10).backgroundColor(0xAFEEEE)
    }.width('100%').margin({ top: 5 })
  }
}
```

![flex](figures/flex.PNG)
