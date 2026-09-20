# Opacity Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-02T11:58:17.187Z -->

Sets the opacity of the component.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

## opacity

opacity(value: number | Resource): T

Sets the opacity of the component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                        |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes   | Opacity of the element. Value range: [0, 1] (percentage). When the value is set to less than 0, the value is 0. When the value is set to greater than 1, the value is 1. 1 indicates fully opaque, and 0 indicates fully transparent, which hides the component but still occupies space in the layout. <br> Default value: 1. When this attribute is not set, the component is fully opaque. <br>**Note:** <br> A child component inherits the opacity of its parent component and superimposes it with its own opacity attribute. For example, if the parent component opacity is 0.1 and the child component opacity is set to 0.8, the actual opacity of the child component is 0.1*0.8=0.08. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## opacity<sup>18+</sup>

opacity(opacity: Optional\<number | Resource>): T

Sets the opacity of the component. Compared with [opacity](#opacity), this API supports the **undefined** type for the **opacity** parameter.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| opacity | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<number&nbsp;\|&nbsp;[Resource](ts-types.md#resource)> | Yes | Opacity of the element. Value range: [0, 1] (percentage). When the value is set to less than 0, the value is 0. When the value is set to greater than 1, the value is 1. 1 indicates fully opaque, and 0 indicates fully transparent. This hides the component but keeps its placeholder in the layout. <br> Default value: 1. When this attribute is not set, the component is fully opaque. <br>**Note:** <br> A child component inherits the opacity of its parent component and combines it with its own opacity attribute. For example, if the parent component opacity is 0.1 and the child component opacity is set to 0.8, the actual opacity of the child component is 0.1*0.8=0.08.<br>When the value of opacity is undefined, the default opacity of 1 is restored. In this case, the default value is still combined with the parent component opacity according to the inheritance rule, that is, the actual opacity of the child component equals the opacity of the parent component. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |


## Example

This example shows how to set the opacity of a component using [opacity](#opacity).

```ts
// xxx.ets
@Entry
@Component
struct OpacityExample {
  build() {
    Column({ space: 5 }) {
      Text('opacity(1)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(1).backgroundColor(0xAFEEEE)
      Text('opacity(0.7)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0.7).backgroundColor(0xAFEEEE)
      Text('opacity(0.4)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0.4).backgroundColor(0xAFEEEE)
      Text('opacity(0.1)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0.1).backgroundColor(0xAFEEEE)
      Text('opacity(0)').fontSize(9).width('90%').fontColor(0xCCCCCC)
      Text().width('90%').height(50).opacity(0).backgroundColor(0xAFEEEE)
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

![opacity.png](figures/opacity.png)
