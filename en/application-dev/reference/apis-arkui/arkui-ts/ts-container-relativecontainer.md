# RelativeContainer

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu; @zhangwentao96-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-19T07:07:28.594Z pushedAt=2026-08-20T10:45:03.047Z -->

Defines a relative layout component used for element alignment in complex scenarios. By setting the alignment rules of child components, it aligns child components relative to the container or other child components. It is suitable for complex UIs that require flexible layout and fewer nesting levels.

Child components can define their alignment rules within the container using [alignRules](./ts-universal-attributes-location.md#alignrules9).

>  **NOTE**
>
> * This component is supported since API version 9. New APIs in later versions are marked with a superscript to indicate their initial version.
> * In the **RelativeContainer** component, when [width](ts-universal-attributes-size.md#width) and [height](ts-universal-attributes-size.md#height) are not set, the layout behavior of the corresponding attributes is the same as when they are set to 100%.
> * Since API version 11, in the **RelativeContainer** component, setting [width](ts-universal-attributes-size.md#width) and [height](ts-universal-attributes-size.md#height) to "auto" means adapting to child components. When width is set to "auto", if a child component uses the container as an anchor in the horizontal direction, "auto" does not take effect (that is, it is treated as if width is not set). The same applies to the vertical direction.
> * Since API version 20, in the **RelativeContainer** component, setting [width](ts-universal-attributes-size.md#width15) and [height](ts-universal-attributes-size.md#height15) to **LayoutPolicy.wrapContent** means adapting to child components while being constrained by the ancestor node size, and setting them to **LayoutPolicy.fixAtIdealSize** means adapting to child components without being constrained by the ancestor node size. When **width** is set to **wrapContent** or **fixAtIdealSize**, if a child component directly or indirectly uses the container as an anchor in the horizontal direction, the container size in that direction does not adapt to that component. The same applies to the vertical direction.
> * The [margin](ts-universal-attributes-size.md#margin) of a child component in **RelativeContainer** differs from the universal margin attribute. It refers to the distance from the child component to the anchor in that direction. For example, when **alignRules** sets a left anchor, **margin.left** indicates the distance from the child component to the left anchor. If **alignRules** does not set an anchor in a certain boundary direction (for example, neither **left** nor **right** anchor is set), the **margin** in that direction does not take effect.

## Child Components

Multiple child components are supported.

## APIs

RelativeContainer()

The **RelativeContainer** component is a container component used for relative layout of elements in complex scenarios.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

> **NOTE**
>
> The **margin** attribute of a child component in **RelativeContainer** has special effective conditions. For details, see the description above.

### guideLine<sup>12+</sup>

guideLine(value: Array&lt;GuideLineStyle&gt;)

Sets the [guidelines](../../../ui/arkts-layout-development-relative-layout.md#positioning-child-components-using-guidelines) in the **RelativeContainer** component. Each element in the array represents a guideline. Typical usage scenarios: aligning child components based on virtual reference lines, creating flexibly adjustable reference lines for positioning, and laying out multiple child components based on the same baseline.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                             |
| ------ | ------------------------------------------ | ---- | --------------------------------- |
| value  | Array<[GuideLineStyle](#guidelinestyle12)>| Yes   | Guideline inside the **RelativeContainer**, which defines the ID, direction, and position of the **guideLine** and is used to assist in positioning child components.|

### barrier<sup>12+</sup>

barrier(value: Array&lt;BarrierStyle&gt;)

Sets the [barriers](../../../ui/arkts-layout-development-relative-layout.md#setting-barriers-for-multiple-components) in the **RelativeContainer** component. Child components can use barriers as anchors for alignment and positioning. Each element in the array represents a barrier. Typical usage scenarios: preventing child components from overlapping, creating virtual boundaries based on component edges, and implementing automatic spacing between components.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description                           |
| ------ | -------------------------------------- | ---- | ------------------------------- |
| value  | Array<[BarrierStyle](#barrierstyle12)> | Yes   | Barrier in the **RelativeContainer** container, used to define the ID, direction, and dependent components of the barrier. Child components can use the barrier as an anchor for alignment and positioning.|

### barrier<sup>12+</sup>

barrier(barrierStyle: Array&lt;LocalizedBarrierStyle&gt;)

Sets barriers in the **RelativeContainer**. Child components can use a barrier as an anchor for alignment and positioning, and barrier lines in mirror mode are supported. Each element in the array represents a barrier. Typical usage: RTL language layout adaptation, mirrored UI design, and automatic adjustment of barrier positions based on the reading direction.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                  | Mandatory| Description                          |
| ------ | -------------------------------------- | ---- | ------------------------------ |
| barrierStyle  | Array<[LocalizedBarrierStyle](#localizedbarrierstyle12)> | Yes   | Barrier in the **RelativeContainer** container, which supports defining barrier lines in mirror mode.|

## GuideLineStyle<sup>12+</sup>

Defines the style of a guideline, which used to define the ID, direction, and position of a guideline, helping child components to be positioned and aligned in the **RelativeContainer**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| id  | string  | No  | No    | ID of the guideline, used to identify the guideline. A child component can reference this guideline as an anchor by using this ID. The ID must be unique and cannot be the same as the name of any component in the container.|
| direction | [Axis](ts-appendix-enums.md#axis) | No  | No    | Direction of the guideline. **Axis.Vertical** indicates a vertical guideline, which can be used only as a horizontal anchor of a component. **Axis.Horizontal** indicates a horizontal guide line, which can be used only as a vertical anchor of a component.<br>Default value: **Axis.Vertical**<br>Invalid value: The default value is used. |
| position | [GuideLinePosition](#guidelineposition12) |  No  | No    | Position of the guideline.<br>If this parameter is not declared or an invalid value (for example, **undefined**) is declared, the position of the guideline defaults to **start: 0**. You can declare either **start** or **end**. If both are declared, only **start** takes effect. If the width of the container is declared as **"auto"**, the position of an **Axis.Vertical** guideline can be declared only by using **start** (percentages are not allowed). If the **height** of the container is declared as **"auto"**, the position of an **Axis.Horizontal** guideline can be declared only by using **start** (percentages are not allowed).<br>Default value:<br>**{<br>start: 0<br>}**<br>Invalid value: The default value is used. |

## GuideLinePosition<sup>12+</sup>

Defines the position of a guideline.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| start  | [Dimension](ts-types.md#dimension10)  | No | Yes    | Distance from the guideline to the left or top edge of the container. Unit: vp.<br>Default value: **0**. Either this parameter or **end** is used. If both are declared, only **start** takes effect. If the **width** of the container is declared as "auto", a guideline of the **Axis.Vertical** type can be declared only in the **start** mode (percentage is not allowed). If the **height** of the container is declared as **"auto"**, a guideline of the **Axis.Horizontal** type can be declared only in the **start** mode (percentage is not allowed).|
| end | [Dimension](ts-types.md#dimension10) | No | Yes   | Distance from the guideline to the right or bottom edge of the container. Unit: vp. Either this parameter or **start** is used. If both are declared, only **start** takes effect. If the **width** of the container is declared as **"auto"**, a guideline of the **Axis.Vertical** type does not support declaration in the **end** mode. If the **height** of the container is declared as **"auto"**, a guideline of the **Axis.Horizontal** type does not support declaration in the **end** mode.|

## BarrierStyle<sup>12+</sup>

Defines the style of a barrier, which is used to define the ID, direction, and dependent components of a barrier. Child components can reference the barrier by its ID as an anchor for alignment and positioning.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| id  | string  | No  | No    | ID of the barrier, used to identify the barrier. A child component can reference this barrier as an anchor by this ID. It must be unique and cannot duplicate the name of any component in the container.|
| direction | [BarrierDirection](#barrierdirection12) | No  | No    | Direction of the barrier.<br>A horizontal barrier line (**TOP**/**BOTTOM**) can serve only as a vertical directional anchor (**top** or **bottom**) of a component. When it is used as a horizontal directional anchor, its position is treated as **0**. A vertical barrier line (**LEFT**/**RIGHT**) can serve only as a horizontal directional anchor (**left** or **right**) of a component. When it is used as a vertical directional anchor, its position is treated as **0**.<br>Default value: **BarrierDirection.LEFT**<br>Invalid value: processed as the default value. |
| referencedId | Array\<string> | No  | No    | Components on which the barrier is generated. Put the IDs of the components that serve as the barrier reference into the array. At least one valid component ID is required. IDs that do not exist are ignored. The barrier position is calculated based on the component boundaries: **LEFT** takes the leftmost, **RIGHT** takes the rightmost, **TOP** takes the topmost, and **BOTTOM** takes the bottommost.|

## BarrierDirection<sup>12+</sup>

Defines the direction of a barrier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value  | Description                         |
| ------ | ---- | ----------------------------- |
| LEFT | 0 | The barrier is at the leftmost position of all its [referencedId](#barrierstyle12). |
| RIGHT | 1 | The barrier is at the rightmost position of all its [referencedId](#barrierstyle12). |
| TOP  | 2 | The barrier is at the topmost position of all its [referencedId](#barrierstyle12). |
| BOTTOM  | 3 | The barrier is at the bottommost position of all its [referencedId](#barrierstyle12). |

## LocalizedBarrierStyle<sup>12+</sup>

Defines the style of a localized barrier, which is used to define the ID, direction, and dependent components of a barrier that supports mirror mode. Child components can reference the barrier by its ID as an anchor for alignment and positioning.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| id  | string  | No  | No   | ID of the barrier, used to identify the barrier. A child component can reference this ID to use the barrier as an anchor. The ID must be unique and must not duplicate the name of any component in the container.|
| localizedDirection | [LocalizedBarrierDirection](#localizedbarrierdirection12) | No  | No    | Direction of the barrier.<br>A horizontal barrier line (**TOP**/**BOTTOM**) can be used only as a vertical directional anchor (**top** or **bottom**) of a component. When it is used as a horizontal directional anchor, its position is treated as **0**. A vertical barrier line (**START**/**END**, supporting LTR/RTL mirroring) can be used only as a horizontal directional anchor (**start** or **end**) of a component. When it is used as a vertical directional anchor, its position is treated as **0**.<br>Default value: **LocalizedBarrierDirection.START**<br>Invalid value: the default value is used.|
| referencedId | Array\<string\> | No  | No   | Components on which the barrier is generated. Put the IDs of the components that serve as the barrier reference into the array. The array must contain at least one valid component ID. IDs that do not exist are ignored. For a barrier that supports mirror mode, the barrier position is calculated based on the actual position in LTR/RTL mode.|

## LocalizedBarrierDirection<sup>12+</sup>

Enumerates the directions of barriers with mirror mode support.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name|  Value | Description                      |
| ------ | -- | ----------------------------- |
| START  | 0  |The barrier is on the start side of all its [referencedId](#localizedbarrierstyle12), that is, the leftmost side in LTR mode and the rightmost side in RTL mode.|
| END    | 1  | The barrier is on the end side of all its [referencedId](#localizedbarrierstyle12), that is, the rightmost side in LTR mode and the leftmost side in RTL mode.|
| TOP    | 2  | The barrier is at the top of all the referenced components specified by [referencedId](#localizedbarrierstyle12).|
| BOTTOM | 3  | The barrier is at the bottom of all the referenced components specified by [referencedId](#localizedbarrierstyle12).|

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example

### Example 1: Implementing a Layout Using Containers and Components as Anchors

This example demonstrates how to use the **alignRules** API to implement a layout with containers and their internal components as anchors.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#a3cf62')
        .alignRules({
          top: { anchor: "__container__", align: VerticalAlign.Top },
          left: { anchor: "__container__", align: HorizontalAlign.Start }
        })
        .id("row1")

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#00ae9d')
        .alignRules({
          top: { anchor: "__container__", align: VerticalAlign.Top },
          right: { anchor: "__container__", align: HorizontalAlign.End }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .height(100)
        .backgroundColor('#0a59f7')
        .alignRules({
          top: { anchor: "row1", align: VerticalAlign.Bottom },
          left: { anchor: "row1", align: HorizontalAlign.End },
          right: { anchor: "row2", align: HorizontalAlign.Start }
        })
        .id("row3")

        Row() {
          Text('row4')
        }.justifyContent(FlexAlign.Center)
        .backgroundColor('#2ca9e0')
        .alignRules({
          top: { anchor: "row3", align: VerticalAlign.Bottom },
          bottom: { anchor: "__container__", align: VerticalAlign.Bottom },
          left: { anchor: "__container__", align: HorizontalAlign.Start },
          right: { anchor: "row1", align: HorizontalAlign.End }
        })
        .id("row4")

        Row() {
          Text('row5')
        }.justifyContent(FlexAlign.Center)
        .backgroundColor('#30c9f7')
        .alignRules({
          top: { anchor: "row3", align: VerticalAlign.Bottom },
          bottom: { anchor: "__container__", align: VerticalAlign.Bottom },
          left: { anchor: "row2", align: HorizontalAlign.Start },
          right: { anchor: "__container__", align: HorizontalAlign.End }
        })
        .id("row5")
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer.png)

### Example 2: Setting Margins for Child Components

This example shows how to set margins for child components in the container.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#a3cf62')
        .alignRules({
          top: { anchor: "__container__", align: VerticalAlign.Top },
          left: { anchor: "__container__", align: HorizontalAlign.Start }
        })
        .id("row1")
        .margin(10)

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.Start },
          top: { anchor: "row1", align: VerticalAlign.Bottom }
        })
        .id("row3")

        Row() {
          Text('row4')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#2ca9e0')
        .alignRules({
          left: { anchor: "row3", align: HorizontalAlign.End },
          top: { anchor: "row2", align: VerticalAlign.Bottom }
        })
        .id("row4")
        .margin(10)
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer1.png)

### Example 3: Configuring the Container to Adapt Its Size to Content

This example shows how to configure the container to adapt its size to content by setting **width** or **height** to **"auto"**.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#a3cf62')
        .id("row1")

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.Start },
          top: { anchor: "row1", align: VerticalAlign.Bottom }
        })
        .id("row3")

        Row() {
          Text('row4')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#2ca9e0')
        .alignRules({
          left: { anchor: "row3", align: HorizontalAlign.End },
          top: { anchor: "row2", align: VerticalAlign.Bottom }
        })
        .id("row4")
      }
      .width("auto").height("auto")
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer2.png)

### Example 4: Applying Vertical Offsets

This example uses [bias](ts-types.md#bias11) to offset the position of a child component between two anchors in the vertical direction.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row()
          .width(100)
          .height(100)
          .backgroundColor('#a3cf62')
          .alignRules({
            top: { anchor: "__container__", align: VerticalAlign.Top },
            bottom: { anchor: "__container__", align: VerticalAlign.Bottom },
            left: { anchor: "__container__", align: HorizontalAlign.Start },
            right: { anchor: "__container__", align: HorizontalAlign.End },
            bias: { vertical: 0.3 }
          })
          .id("row1")
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer3.png)

### Example 5: Setting Guidelines

This example demonstrates how to set guidelines in a relative layout using the [guideLine](#guideline12) API, with child components using these guidelines as anchors.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row()
          .width(100)
          .height(100)
          .backgroundColor('#a3cf62')
          .alignRules({
            left: { anchor: "guideline1", align: HorizontalAlign.End },
            top: { anchor: "guideline2", align: VerticalAlign.Top }
          })
          .id("row1")
      }
      .width(300)
      .height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
      .guideLine([{ id: "guideline1", direction: Axis.Vertical, position: { start: 50 } },
        { id: "guideline2", direction: Axis.Horizontal, position: { start: 50 } }])
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer4.png)

### Example 6: Implementing Barriers

This example shows how to set barriers in a relative layout using the [barrier](#barrier12) API, with child components using these barriers as anchors.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#a3cf62')
        .id("row1")

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#00ae9d')
        .alignRules({
          middle: { anchor: "row1", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Bottom }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "barrier1", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row3")

        Row() {
          Text('row4')
        }
        .justifyContent(FlexAlign.Center)
        .width(50)
        .height(50)
        .backgroundColor('#2ca9e0')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.Start },
          top: { anchor: "barrier2", align: VerticalAlign.Bottom }
        })
        .id("row4")
      }
      .width(300)
      .height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
      .barrier([{ id: "barrier1", direction: BarrierDirection.RIGHT, referencedId: ["row1", "row2"] },
        { id: "barrier2", direction: BarrierDirection.BOTTOM, referencedId: ["row1", "row2"] }])
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer5.png)

### Example 7: Creating Chains

This example uses the [chainMode](ts-universal-attributes-location.md#chainmode12) API to implement a horizontal [SPREAD](ts-universal-attributes-location.md#chainstyle12) chain, a [SPREAD_INSIDE](ts-universal-attributes-location.md#chainstyle12) chain, and a [PACKED](ts-universal-attributes-location.md#chainstyle12) chain from top to bottom.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#a3cf62')
        .alignRules({
          left: { anchor: "__container__", align: HorizontalAlign.Start },
          right: { anchor: "row2", align: HorizontalAlign.Start },
          top: { anchor: "__container__", align: VerticalAlign.Top }
        })
        .id("row1")
        .chainMode(Axis.Horizontal, ChainStyle.SPREAD)

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.End },
          right: { anchor: "row3", align: HorizontalAlign.Start },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row2", align: HorizontalAlign.End },
          right: { anchor: "__container__", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row3")

        Row() {
          Text('row4')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#a3cf62')
        .alignRules({
          left: { anchor: "__container__", align: HorizontalAlign.Start },
          right: { anchor: "row5", align: HorizontalAlign.Start },
          center: { anchor: "__container__", align: VerticalAlign.Center }
        })
        .id("row4")
        .chainMode(Axis.Horizontal, ChainStyle.SPREAD_INSIDE)

        Row() {
          Text('row5')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row4", align: HorizontalAlign.End },
          right: { anchor: "row6", align: HorizontalAlign.Start },
          top: { anchor: "row4", align: VerticalAlign.Top }
        })
        .id("row5")

        Row() {
          Text('row6')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row5", align: HorizontalAlign.End },
          right: { anchor: "__container__", align: HorizontalAlign.End },
          top: { anchor: "row4", align: VerticalAlign.Top }
        })
        .id("row6")

        Row() {
          Text('row7')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#a3cf62')
        .alignRules({
          left: { anchor: "__container__", align: HorizontalAlign.Start },
          right: { anchor: "row8", align: HorizontalAlign.Start },
          bottom: { anchor: "__container__", align: VerticalAlign.Bottom }
        })
        .id("row7")
        .chainMode(Axis.Horizontal, ChainStyle.PACKED)

        Row() {
          Text('row8')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row7", align: HorizontalAlign.End },
          right: { anchor: "row9", align: HorizontalAlign.Start },
          top: { anchor: "row7", align: VerticalAlign.Top }
        })
        .id("row8")

        Row() {
          Text('row9')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row8", align: HorizontalAlign.End },
          right: { anchor: "__container__", align: HorizontalAlign.End },
          top: { anchor: "row7", align: VerticalAlign.Top }
        })
        .id("row9")
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer6.png)

### Example 8: Creating a Chain with Offsets

This example uses the [chainMode](ts-universal-attributes-location.md#chainmode12) and [bias](ts-types.md#bias11) APIs to implement a horizontally biased [PACKED](ts-universal-attributes-location.md#chainstyle12) chain.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#a3cf62')
        .alignRules({
          left: { anchor: "__container__", align: HorizontalAlign.Start },
          right: { anchor: "row2", align: HorizontalAlign.Start },
          center: { anchor: "__container__", align: VerticalAlign.Center },
          bias: { horizontal: 0 }
        })
        .id("row1")
        .chainMode(Axis.Horizontal, ChainStyle.PACKED)

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.End },
          right: { anchor: "row3", align: HorizontalAlign.Start },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row2", align: HorizontalAlign.End },
          right: { anchor: "__container__", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row3")
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer7.png)

### Example 9: Implementing a Mirror Effect

This example demonstrates how to use [LocalizedAlignRuleOptions](ts-universal-attributes-location.md#localizedalignruleoptions12) and [LocalizedBarrierDirection](#localizedbarrierdirection12) for alignment when using barriers as anchors in mirror mode (**direction** set to **Direction.Rtl**).

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#a3cf62')
        .id("row1")

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#00ae9d')
        .alignRules({
          middle: { anchor: "row1", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Bottom }
        })
        .id("row2")

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(100)
        .height(100)
        .backgroundColor('#0a59f7')
        .alignRules({
          start: { anchor: "barrier1", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row3")

        Row() {
          Text('row4')
        }
        .justifyContent(FlexAlign.Center)
        .width(50)
        .height(50)
        .backgroundColor('#2ca9e0')
        .alignRules({
          start: { anchor: "row1", align: HorizontalAlign.Start },
          top: { anchor: "barrier2", align: VerticalAlign.Bottom }
        })
        .id("row4")
      }
      .direction(Direction.Rtl)
      .width(300)
      .height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
      .barrier([{ id: "barrier1", localizedDirection: LocalizedBarrierDirection.END, referencedId: ["row1", "row2"] },
        { id: "barrier2", localizedDirection: LocalizedBarrierDirection.BOTTOM, referencedId: ["row1", "row2"] }])
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer8.png)

### Example 10: Setting Component Weights in a Chain

This example demonstrates how to use [chainWeight](ts-universal-attributes-location.md#chainweight14) to set the size weights of components in a chain.

You must first set the chain alignment rules of child components through **alignRules** (to ensure that the components form a chain in the horizontal or vertical direction), and then set the chain style (such as **SPREAD**, **SPREAD_INSIDE**, and **PACKED**) through **chainMode**. **chainWeight** takes effect only in chain mode.

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      RelativeContainer() {
        Row() {
          Text('row1')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#a3cf62')
        .alignRules({
          left: { anchor: "__container__", align: HorizontalAlign.Start },
          right: { anchor: "row2", align: HorizontalAlign.Start },
          center: { anchor: "__container__", align: VerticalAlign.Center },
        })
        .id("row1")
        .chainMode(Axis.Horizontal, ChainStyle.PACKED)

        Row() {
          Text('row2')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#00ae9d')
        .alignRules({
          left: { anchor: "row1", align: HorizontalAlign.End },
          right: { anchor: "row3", align: HorizontalAlign.Start },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row2")
        .chainWeight({ horizontal: 1 })

        Row() {
          Text('row3')
        }
        .justifyContent(FlexAlign.Center)
        .width(80)
        .height(80)
        .backgroundColor('#0a59f7')
        .alignRules({
          left: { anchor: "row2", align: HorizontalAlign.End },
          right: { anchor: "__container__", align: HorizontalAlign.End },
          top: { anchor: "row1", align: VerticalAlign.Top }
        })
        .id("row3")
        .chainWeight({ horizontal: 2 })
      }
      .width(300).height(300)
      .margin({ left: 50 })
      .border({ width: 2, color: "#6699FF" })
    }
    .height('100%')
  }
}
```

![relative container](figures/relativecontainer9.png)
<!--no_check-->