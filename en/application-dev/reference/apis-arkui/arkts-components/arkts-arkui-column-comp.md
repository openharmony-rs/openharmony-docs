# Column

A container that lays out child components along the vertical direction. It is suitable for scenarios where multiple child components need to be arranged sequentially in the vertical direction, such as list items, form items, and card content. It supports setting attributes such as child component spacing and alignment, enabling quick implementation of vertical linear layout.

> **NOTE** > > If no height or width is set for the **Column** component, it adapts to the size of child components in the main > axis (vertical direction) or cross axis (horizontal direction).

## Child Components

Supported

## Column

```TypeScript
Column(options?: ColumnOptions)
```

Creates a vertical linear layout container. You can set the spacing between child components.

> **NOTE:** 
> 
> When using multi-component nesting in complex UIs, if layout components are nested too deeply or too many
> components are nested, additional overhead will be incurred. It is recommended to optimize performance by
> removing redundant nodes, using layout boundaries to reduce layout calculations, and properly adopting rendering
> control syntax and layout component methods.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ColumnOptions](arkts-arkui-column-comp-columnoptions-i.md) | No | Spacing configuration options of the **Column** component. It sets the vertical spacing between elements in the column layout through the **space** attribute. Pass this parameter when a fixed vertical spacing needs to be set for child components; if omitted, no child component spacing is set.<br> |

## Column

```TypeScript
Column(options?: ColumnOptions | ColumnOptionsV2)
```

Creates a vertical linear layout container. You can set the spacing between child components.

> **NOTE:** 
> 
> When using multi-component nesting in complex UIs, if layout components are nested too deeply or too many
> components are nested, additional overhead will be incurred. It is recommended to optimize performance by
> removing redundant nodes, using layout boundaries to reduce layout calculations, and properly adopting rendering
> control syntax and layout component methods.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ColumnOptions](arkts-arkui-column-comp-columnoptions-i.md) &#124; [ColumnOptionsV2](arkts-arkui-column-comp-columnoptionsv2-i.md) | No | Spacing configuration options of the **Column** component. The **space** attribute sets the vertical spacing between elements in the column layout. **space** supports settings of the number, string, or Resource type. Pass this parameter when a fixed vertical spacing needs to be set for child components; if omitted, no child component spacing is set. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ColumnOptions](arkts-arkui-column-comp-columnoptions-i.md) | Sets the spacing between child components of the **Column** component. |
| [ColumnOptionsV2](arkts-arkui-column-comp-columnoptionsv2-i.md) | Sets the spacing between child components of the **Column** component. The spacing type **SpaceType** can be number, string, or Resource. |

### Types

| Name | Description |
| --- | --- |
| [SpaceType](arkts-arkui-column-comp-spacetype-t.md) | Describes the supported data types for the **space** parameter in the constructors of the **Column** component. The type is a union of the following types. |

## Examples

### Example 1: Setting the Layout Attributes of the Column Component

This example demonstrates how to set the layout attributes of the Column component, such as the spacing and alignment mode, and its effect.

```TypeScript
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



```TypeScript
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
