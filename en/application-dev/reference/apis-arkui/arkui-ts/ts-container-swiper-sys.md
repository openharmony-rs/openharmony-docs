# Swiper (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @Hu_ZeQi-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=17ea35c4d061710d52b9f90a2c92de1c605c8696 translatedAt=2026-08-19T07:25:16.949Z pushedAt=2026-08-20T10:45:03.057Z -->

The **Swiper** component is a container that provides the scrolling carousel display capability for its child components.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs of this module. For details about its public APIs, see [Swiper](ts-container-swiper.md).

## Attributes

### ignoreHiddenItem

ignoreHiddenItem(enabled: boolean)

Sets whether a child component occupies space in the viewport when its [visibility](ts-universal-attributes-visibility.md#visibility) attribute is set to **Visibility.None**.

> **NOTE**
>
> This API does not take effect when the [loop](ts-container-swiper.md#loop) attribute is set to **true**, or when the **swipeByGroup** parameter of the [displayCount](ts-container-swiper.md#displaycount22) attribute is set to **true**.

**Since**: 26.0.0

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| enabled | boolean | Yes | Whether a child component occupies space in the viewport when its **visibility** attribute is set to **Visibility.None**.<br/>Default value: **false**<br/>**true**: The hidden child component does not occupy space in the viewport.<br/>**false**: The hidden child component still occupies space in the viewport.<br/>An invalid value is handled as **false**. |

## Examples

This example shows how the **Swiper** component prevents a child component from occupying space when it is set to invisible by using the [ignoreHiddenItem](#ignorehiddenitem) API.

The [ignoreHiddenItem](#ignorehiddenitem) API is added since API version 26.0.0.

```ts
// xxx.ets
@Entry
@Component
struct IgnoreHiddenItemSample {
  private swiperController: SwiperController = new SwiperController();

  build() {
    Column() {
      Swiper(this.swiperController) {
        Text('1')
          .width('100%')
          .height(160)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
          .fontSize(30)
        Text('2')
          .width('100%')
          .height(160)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
          .fontSize(30)
          .visibility(Visibility.None)
        Text('3')
          .width('100%')
          .height(160)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
          .fontSize(30)
      }
      .width('100%')
      .height(200)
      .loop(false)
      .indicator(false)
      .ignoreHiddenItem(true)
      .curve(Curve.Linear)
      .duration(2000)

      Button('change to index 2').onClick(() => {
        this.swiperController.changeIndex(2, true)
      })
    }
  }
}
```

<!--Del--> <!--DelEnd-->