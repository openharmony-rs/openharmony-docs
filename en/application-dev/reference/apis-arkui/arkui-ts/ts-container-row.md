# Row
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

The **Row** component lays out child components horizontally.

>  **NOTE**
>
>  This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
>  If no width or height is set for the **Row** component, the component automatically adapts to the size of its child components in the main axis and cross axis respectively.


## Child Components

Supported


## APIs
### Row

Row(options?: RowOptions)

Creates a horizontal linear layout container. You can set the spacing between child components.

>  **NOTE**
>
>  Excessive component nesting (either too deep a hierarchy or too many nested components) incurs significant performance overhead. For performance purposes, you are advised to remove redundant nodes to simplify the component tree, use layout boundaries to reduce redundant layout calculations, properly apply rendering control syntax and layout component methods to minimize unnecessary re-renders and computations. For details about the best practices, see [Layout Optimization](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve-layout-performance).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options<sup>18+</sup> | [RowOptions](#rowoptions18) | No| Spacing between elements in the horizontal layout. The value can be of the number or string type.|

### Row<sup>18+</sup>
Row(options?: RowOptions | RowOptionsV2)

Creates a horizontal linear layout container. You can set the spacing between child components.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [RowOptions](#rowoptions18)  \| [RowOptionsV2](#rowoptionsv218) | No| Spacing between elements in a horizontal layout. The value can be of the number, string, or Resource type.|

## RowOptions<sup>18+</sup>

Sets the spacing between child components of the **Row** component.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| space<sup>7+</sup> | string \| number | No| Yes| Spacing between child components.<br>Since API version 9, this parameter does not take effect when it is set to a negative number or when **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround** or **FlexAlign.SpaceEvenly**.<br>Default value: **0**<br>Unit: vp.<br>Invalid values are treated as the default value.<br>**NOTE**<br>The value of **space** can be a number greater than or equal to 0 or a string that can be converted to a number.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## RowOptionsV2<sup>18+</sup>

Sets the spacing between child components of the **Row** component. The spacing type **SpaceType** can be number, string, or Resource.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| space | [SpaceType](ts-container-column.md#spacetype18) | No| Yes| Spacing between child components.<br>This parameter does not take effect if the value specified is a negative number, or if **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**.<br>Default value: **0**<br>Unit: vp.<br>Invalid values are treated as the default value.<br>**NOTE**<br>The value of **space** can be a number greater than or equal to 0, a string that can be converted to a number, or a Resource type that can be converted to a number.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### alignItems

alignItems(value: VerticalAlign)

Sets the alignment mode of child components in the vertical direction.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [VerticalAlign](ts-appendix-enums.md#verticalalign) | Yes  | Alignment mode of child components in the vertical direction.<br>Default value: **VerticalAlign.Center**|

### justifyContent<sup>8+</sup>

justifyContent(value: FlexAlign)

Sets the alignment mode of the child components in the horizontal direction.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                      |
| ------ | ------------------------------------------- | ---- | ---------------------------------------------------------- |
| value  | [FlexAlign](ts-appendix-enums.md#flexalign) | Yes  | Alignment mode of child components in the horizontal direction.<br>Default value: **FlexAlign.Start**|

>  **NOTE**
>
>  During the row layout, if [flexShrink](ts-universal-attributes-flex-layout.md#flexshrink) is not set for a child component, the child component is not compressed by default. This can result in the total main axis size of all child components exceeding the container's main axis size, which makes **FlexAlign.Center** and **FlexAlign.End** ineffective.

### reverse<sup>12+</sup>

reverse(isReversed: Optional\<boolean\>)

Sets whether to reverse the horizontal arrangement of child components.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                      |
| ------ | ------------------------------------------- | ---- | ---------------------------------------------------------- |
| isReversed  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean\> | Yes  | Whether to reverse the horizontal arrangement of child components.<br>Default value: **true**. **true**: Child components are arranged in reverse order horizontally. **false**: Child components are arranged in normal order horizontally.|

>  **NOTE**
>
>  If the **reverse** attribute is not set, the arrangement on the main axis remains in the normal order. If the attribute is set to **undefined**, it defaults to **true**, which reverses the arrangement on the main axis.<br>Keep in mind that the main axis arrangement direction is also affected by the **direction** attribute. If **reverse** is set to **true**, it effectively reverses the arrangement that results from the **direction** attribute settings.

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example

### Example 1: Setting the Layout Attributes of the Row Component

This example demonstrates how to set the layout attributes of the **Row** component, such as the spacing and alignment mode and its effect.

```json
// resources/base/element/string.json
{
  "string": [
    {
      "name": "stringSpace",
      "value": "5"
    }
  ]
}
```

```ts
// xxx.ets
@Entry
@Component
struct RowExample {
  build() {
    Column({ space: 5 }) {
      // Set the horizontal spacing between two adjacent child components to 5.
      Text('space').width('90%')
      Row({ space: 5 }) {
        Row().width('30%').height(50).backgroundColor(0xAFEEEE)
        Row().width('30%').height(50).backgroundColor(0x00FFFF)
      }.width('90%').height(107).border({ width: 1 })

      // Set the spacing between child components using the Resource type.
      Text('Resource space').width('90%')
      Row({ space: $r('app.string.stringSpace') }) {
        Row().width('30%').height(50).backgroundColor(0xAFEEEE)
        Row().width('30%').height(50).backgroundColor(0x00FFFF)
      }.width('90%').height(107).border({ width: 1 })

      // Set the alignment mode of the child components in the vertical direction.
      Text('alignItems(Bottom)').width('90%')
      Row() {
        Row().width('30%').height(50).backgroundColor(0xAFEEEE)
        Row().width('30%').height(50).backgroundColor(0x00FFFF)
      }.width('90%').alignItems(VerticalAlign.Bottom).height('15%').border({ width: 1 })

      Text('alignItems(Center)').width('90%')
      Row() {
        Row().width('30%').height(50).backgroundColor(0xAFEEEE)
        Row().width('30%').height(50).backgroundColor(0x00FFFF)
      }.width('90%').alignItems(VerticalAlign.Center).height('15%').border({ width: 1 })

      // Set the alignment mode of the child components in the horizontal direction.
      Text('justifyContent(End)').width('90%')
      Row() {
        Row().width('30%').height(50).backgroundColor(0xAFEEEE)
        Row().width('30%').height(50).backgroundColor(0x00FFFF)
      }.width('90%').border({ width: 1 }).justifyContent(FlexAlign.End)

      Text('justifyContent(Center)').width('90%')
      Row() {
        Row().width('30%').height(50).backgroundColor(0xAFEEEE)
        Row().width('30%').height(50).backgroundColor(0x00FFFF)
      }.width('90%').border({ width: 1 }).justifyContent(FlexAlign.Center)
    }.width('100%')
  }
}
```

![row](figures/row.png)

### Example 2: Configuring the Reverse Attribute

This example demonstrates how to set the **reverse** attribute of the **Row** component and its effect.

```ts
@Entry
@Component
struct RowReverseSample {
  build() {
    Row() {
      Text("1")
        .width(100)
        .height(50)
        .backgroundColor(0xAFEEEE)

      Text("2")
        .width(100)
        .height(50)
        .backgroundColor(0x00FFFF)
    }
    .height(100)
    .width(300)
    .border({ width: 1 })
    .reverse(true)
  }
}
```

![row](figures/row_reverse.png)
