# Column
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

The **Column** component lays out child components vertically.

>  **NOTE**
>
>  This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
>  If no height or width is set for the **Column** component, the component automatically adapts to the size of its child components in the main axis and cross axis respectively.


## Child Components

Supported


## APIs

### Column
Column(options?: ColumnOptions)

Creates a vertical linear layout container. You can set the spacing between child components.

>  **NOTE**
>
>  Excessive component nesting (either too deep a hierarchy or too many nested components) incurs significant performance overhead. For performance purposes, you are advised to remove redundant nodes to simplify the component tree, use layout boundaries to reduce redundant layout calculations, properly apply rendering control syntax and layout component methods to minimize unnecessary re-renders and computations. For details about the best practices, see [Layout Optimization](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve-layout-performance).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options<sup>18+</sup> | [ColumnOptions](#columnoptions18)| No| Vertical spacing between two adjacent child components. The value can be of the number or string type.|

### Column<sup>18+</sup>
Column(options?: ColumnOptions | ColumnOptionsV2)

Creates a vertical linear layout container. You can set the spacing between child components.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [ColumnOptions](#columnoptions18) \| [ColumnOptionsV2](#columnoptionsv218) | No| Vertical spacing between two adjacent child components. The value can be of the number, string, or Resource type.|

## ColumnOptions<sup>18+</sup>

Sets the spacing between child components of the **Column** component.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| space<sup>7+</sup> | string&nbsp;\|&nbsp;number | No| Yes| Vertical spacing between two adjacent child components.<br>This parameter has no effect if the value specified is a negative number, or if [justifyContent](ts-container-column.md#justifycontent8) is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**<br>Default value: **0**<br>Invalid values are treated as the default value.<br>Unit: vp<br>**NOTE**<br>The value of **space** can be a number greater than or equal to 0 or a string that can be converted to a number.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## ColumnOptionsV2<sup>18+</sup>

Sets the spacing between child components of the **Column** component. The spacing type **SpaceType** can be number, string, or Resource.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| space | [SpaceType](#spacetype18) | No| Yes| Vertical spacing between two adjacent child components.<br>This parameter has no effect if the value specified is a negative number, or if **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**.<br>Default value: **0**<br>Unit: vp<br>Invalid values are treated as the default value.<br>**NOTE**<br>The value of **space** can be a number greater than or equal to 0, a string that can be converted to a number, or a Resource type that can be converted to a number.|

## SpaceType<sup>18+</sup>

type SpaceType = string | number | Resource

Describes the supported data types for the **space** parameter in the constructors of the **Column** component. The type is a union of the following types.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Type|Description|
|---|---|
|number|Represents a numeric value. It can take any numerical value.|
|string|Represents a string value. It can take any string value.|
|[Resource](ts-types.md#resource)|Represents a resource reference type. It can take values from system resources or application resources.|


## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### alignItems

alignItems(value: HorizontalAlign)

Alignment mode of the child components in the horizontal direction.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [HorizontalAlign](ts-appendix-enums.md#horizontalalign) | Yes  | Alignment mode of child components in the horizontal direction.<br>Default value: **HorizontalAlign.Center**|

### justifyContent<sup>8+</sup>

justifyContent(value: FlexAlign)

Alignment mode of the child components in the vertical direction.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                      |
| ------ | ------------------------------------------- | ---- | ---------------------------------------------------------- |
| value  | [FlexAlign](ts-appendix-enums.md#flexalign) | Yes  | Alignment mode of child components in the vertical direction.<br>Default value: **FlexAlign.Start**|

>  **NOTE**
>
>  During the column layout, if [flexShrink](ts-universal-attributes-flex-layout.md#flexshrink) is not set for a child component, the child component is not compressed by default. This can result in the total main axis size of all child components exceeding the container's main axis size, which makes **FlexAlign.Center** and **FlexAlign.End** ineffective.

### reverse<sup>12+</sup>

reverse(isReversed: Optional\<boolean\>)

Sets whether to reverse the vertical arrangement of child components.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                      |
| ------ | ------------------------------------------- | ---- | ---------------------------------------------------------- |
| isReversed  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean\> | Yes  | Whether to reverse the vertical arrangement of child components.<br>Default value: **true**. **true**: Child components are arranged in reverse order vertically. **false**: Child components are arranged in normal order vertically.|

>  **NOTE**
>
>  If the **reverse** attribute is not set, the arrangement on the main axis remains in the normal order. If the attribute is set to **undefined**, it defaults to **true**, which reverses the arrangement on the main axis.<br>The **direction** attribute only changes the cross axis direction of the column and does not impact the main axis direction. Therefore, it is independent of the **reverse** attribute.

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example

### Example 1: Setting the Layout Attributes of the Column Component

This example demonstrates how to set the layout attributes of the **Column** component, such as the spacing and alignment mode and its effect.

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
struct ColumnExample {
  build() {
    Scroll() {
      Column({ space: 5 }) {
        // Set the vertical spacing between two adjacent child components to 5.
        Text('space').width('90%')
        Column({ space: 5 }) {
          Column().width('100%').height(30).backgroundColor(0xAFEEEE)
          Column().width('100%').height(30).backgroundColor(0x00FFFF)
        }.width('90%').height(100).border({ width: 1 })

        // Set the spacing between child elements using the Resource type.
        Text('Resource space').width('90%')
        Column({ space: $r('app.string.stringSpace') }) {
          Column().width('100%').height(30).backgroundColor(0xAFEEEE)
          Column().width('100%').height(30).backgroundColor(0x00FFFF)
        }.width('90%').height(100).border({ width: 1 })

        // Set the alignment mode of the child components in the horizontal direction.
        Text('alignItems(Start)').width('90%')
        Column() {
          Column().width('50%').height(30).backgroundColor(0xAFEEEE)
          Column().width('50%').height(30).backgroundColor(0x00FFFF)
        }.alignItems(HorizontalAlign.Start).width('90%').border({ width: 1 })

        Text('alignItems(End)').width('90%')
        Column() {
          Column().width('50%').height(30).backgroundColor(0xAFEEEE)
          Column().width('50%').height(30).backgroundColor(0x00FFFF)
        }.alignItems(HorizontalAlign.End).width('90%').border({ width: 1 })

        Text('alignItems(Center)').width('90%')
        Column() {
          Column().width('50%').height(30).backgroundColor(0xAFEEEE)
          Column().width('50%').height(30).backgroundColor(0x00FFFF)
        }.alignItems(HorizontalAlign.Center).width('90%').border({ width: 1 })

        // Set the alignment mode of the child components in the vertical direction.
        Text('justifyContent(Center)').width('90%')
        Column() {
          Column().width('90%').height(30).backgroundColor(0xAFEEEE)
          Column().width('90%').height(30).backgroundColor(0x00FFFF)
        }.height(100).border({ width: 1 }).justifyContent(FlexAlign.Center)

        Text('justifyContent(End)').width('90%')
        Column() {
          Column().width('90%').height(30).backgroundColor(0xAFEEEE)
          Column().width('90%').height(30).backgroundColor(0x00FFFF)
        }.height(100).border({ width: 1 }).justifyContent(FlexAlign.End)
      }.width('100%').padding({ top: 5 })
    }.width('100%').height('100%')
  }
}
```

![column](figures/column.png)

### Example 2: Configuring the Reverse Attribute

This example demonstrates how to set the **reverse** attribute of the **Column** component and its effect.

```ts
@Entry
@Component
struct ColumnReverseSample {
  build() {
    Column() {
      Text("1")
        .width(50)
        .height(100)
        .backgroundColor(0xAFEEEE)

      Text("2")
        .width(50)
        .height(100)
        .backgroundColor(0x00FFFF)
    }
    .height(300)
    .width(100)
    .border({ width: 1 })
    .reverse(true)
  }
}
```

![column](figures/column_reverse.png)
