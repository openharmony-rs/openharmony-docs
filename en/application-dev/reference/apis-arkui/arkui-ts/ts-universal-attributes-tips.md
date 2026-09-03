# Tooltip Control

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=680bf7716703da5d9a1a9e8718e14287307af1ba translatedAt=2026-08-24T07:03:05.125Z pushedAt=2026-08-25T07:34:57.855Z -->

You can bind a floating tooltip to a component. The tooltip automatically appears when a pointer hovers over the component and disappears when the pointer moves away.

> **NOTE**
>
> - This API is supported since API version 19. Newly added content in later versions is marked with a superscript to indicate the version in which it was introduced.
>
> - The APIs of this module can be used only in the stage model.
>
> - Tips control depends on the device being able to trigger [hover events](./ts-universal-events-hover.md). Tips control cannot be used on hardware devices that cannot trigger [hover events](./ts-universal-events-hover.md).

## bindTips

bindTips(message: TipsMessageType, options?: TipsOptions): T

Binds a tooltip to the component.

> **NOTE**
>
> When the [enabled](ts-universal-attributes-enable.md#enabled) universal attribute of the component bound with **bindTips** is set to **false**, the floating bubble can still be displayed.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| message|  [TipsMessageType](#tipsmessagetype)                                                     | Mandatory   | Content of the floating bubble. |
| options  | [TipsOptions](#tipsoptions) | No  | Parameters of the tooltip.<br>Default value:<br>{<br>appearingTime: 700,<br>disappearingTime: 300,<br>appearingTimeWithContinuousOperation: 300,<br>disappearingTimeWithContinuousOperation: 0, enableArrow: true,<br>arrowPointPosition: ArrowPointPosition.CENTER,<br>arrowWidth: 16,arrowHeight: 8,<br>showAtAnchor: TipsAnchorType.TARGET<br>} |

**Return value**

|Type|Description|
|---|---|
|T|Current component.|

## TipsOptions

Defines the parameters of the tooltip.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                 | Type                                                        | Read-Only| Optional| Description                                                     |
| ------------------------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| appearingTime         |           number   | No   | Yes |Delay before the tooltip appears. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.<br>Default value: **700**.<br>Unit: ms.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| disappearingTime                 |   number   | No  | Yes | Delay before the tooltip disappears. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.<br>Default value: **300**.<br>Unit: ms.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| appearingTimeWithContinuousOperation    |     number   | No  | Yes | Delay before the tooltip appears when multiple tooltips are displayed consecutively. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.<br>Default value: **300**.<br>Unit: ms.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| disappearingTimeWithContinuousOperation |     number   | No  | Yes | Delay before the tooltip disappears when multiple tooltips are displayed consecutively. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.<br>Default value: **0**.<br>Unit: ms.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| enableArrow        | boolean                                                      | No  | Yes | Whether to display the tooltip arrow.<br>Default value: **true**.<br>**true**: yes. **false**: no.<br>**NOTE**<br>If the available space on the screen is insufficient, the tooltip will cover part of the component and the arrow will not be displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| arrowPointPosition     | [ArrowPointPosition](ts-appendix-enums.md#arrowpointposition11) | No   | Yes  | Position of the tooltip arrow relative to the parent component. The bubble arrow has three optional positions in the vertical and horizontal directions: **Start**, **Center**, and **End**. All positions are within the parent component area, and do not exceed the boundary of the parent component or cover the rounded corner area.<br/>Default value: **ArrowPointPosition.CENTER**<br/>**Atomic service API:** This API can be used in atomic services since API version 19. |
| arrowWidth           | [Dimension](ts-types.md#dimension10)                  | No  | Yes | Width of the tooltip arrow. If the set width exceeds the length of the edge minus twice the tooltip's corner radius, the arrow is not drawn.<br>Default value: **16**.<br>Unit: vp.<br>**NOTE**<br>Percentage values are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| arrowHeight          | [Dimension](ts-types.md#dimension10)                  | No  | Yes | Height of the tooltip arrow.<br>Default value: **8**.<br>Unit: vp.<br>**NOTE**<br>Percentage values are not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|
| showAtAnchor<sup>20+</sup> | [TipsAnchorType](ts-appendix-enums.md#tipsanchortype20)                  | No  | Yes | Anchor type of the tooltip.<br>Default value: **TipsAnchorType.TARGET**.<br>**NOTE**<br>If the anchor type of the tooltip is **TipsAnchorType.CURSOR**, the tooltip does not display an arrow.<br>**Atomic service API**: This API can be used in atomic services since API version 20.   |
| systemMaterial |  [SystemUiMaterial](ts-universal-attributes-image-effect.md#systemuimaterial) | No | Yes  |System material of the tooltip.<br/>Default value: undefined, which clears the material effect set by this API. <br/>**NOTE**<br />Different system materials have different effects on attributes. This API affects background color [backgroundColor](ts-universal-attributes-background.md#backgroundcolor), border color [borderColor](ts-universal-attributes-border.md#bordercolor), border width [borderWidth](ts-universal-attributes-border.md#borderwidth), and shadow [shadow](ts-universal-attributes-image-effect.md#shadow). When a system material is set, the preceding APIs do not take effect.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model.<br/>**Atomic service API:** This API can be used in atomic services since API version 26.0.0. |

## TipsMessageType

type TipsMessageType = ResourceStr | StyledString

Defines the type of the tooltip message.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                                      | Description                                          |
| ---------------------------------------------------------- | ---------------------------------------------- |
| [ResourceStr](ts-types.md#resourcestr)                     | Type used to represent the types that can be used by input parameters of the string type.|
| [StyledString](ts-universal-styled-string.md#styledstring) | Styled string.                                  |

## Example

You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

### Example 1: Binding a Tooltip

This example shows how to bind a tooltip to a button using **bindTips**.

```ts
// xxx.ets
@Entry
@Component
struct TipsExample {
  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Hover Tips')
        .bindTips("Tips", {
          appearingTime: 700,
          disappearingTime: 300,
          appearingTimeWithContinuousOperation: 300,
          disappearingTimeWithContinuousOperation: 0,
          enableArrow: true,
        })
        .position({ x: 100, y: 250 })
    }.width('100%').padding({ top: 5 })
  }
}
```

![](figures/tips01.gif)

### Example 2: Displaying and Hiding Multiple Tooltips

This example demonstrates how to configure multiple tooltips to appear and disappear in sequence using **bindTips**.

```ts
// xxx.ets

@Entry
@Component
struct TipsExample {
  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Hover Tips')
        .bindTips("Tips", {
          appearingTime: 700,
          disappearingTime: 300,
          appearingTimeWithContinuousOperation: 300,
          disappearingTimeWithContinuousOperation: 0,
          enableArrow: true,
        })
        .position({ x: 100, y: 250 })

      Button('Hover Tips')
        .bindTips("Tips", {
          appearingTime: 700,
          disappearingTime: 300,
          appearingTimeWithContinuousOperation: 300,
          disappearingTimeWithContinuousOperation: 0,
          enableArrow: true,
        })
        .position({ x: 100, y: 350 })


    }.width('100%').padding({ top: 5 })
  }
}
```

![](figures/tips02.gif)

### Example 3: Setting the System Material Effect of a Tooltip

This example implements the system material effect of **bindTips** by setting the **systemMaterial** attribute in [TipsOptions](#tipsoptions).

Since API version 26.0.0, the **systemMaterial** attribute is added to **TipsOptions**.

```ts
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct TipsExample {
  build() {
    Flex({ direction: FlexDirection.Column }) {
      Button('Hover Tips')
        .bindTips("Floating Bubble Test", {
          // Control whether to set the system material.
          systemMaterial: new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THIN
          })
        })
        .position({ x: 100, y: 300 })
    }.width('100%').padding({ top: 5 })
    // Replace it with the actual resource file.
    .backgroundImage($r("app.media.img"))
    .backgroundImageSize({width: '100%', height: '100%'})
  }
}
```

When the system material is not set:

<!--Del--> <!--DelEnd-->

After the system material is set:

<!--Del--> <!--DelEnd-->