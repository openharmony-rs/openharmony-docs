# 气泡提示（Popup）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->
Popup属性可绑定在组件上显示气泡弹窗提示，设置弹窗内容、交互逻辑和显示状态。主要用于屏幕录制、信息弹出提醒等显示状态。

气泡分为两种类型，一种是系统提供的气泡[PopupOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions类型说明)，一种是开发者可以自定义的气泡[CustomPopupOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#custompopupoptions8类型说明)。其中，PopupOptions通过配置primaryButton和secondaryButton来设置带按钮的气泡；CustomPopupOptions通过配置[builder](../../application-dev/ui/state-management/arkts-builder.md)来设置自定义的气泡。其中系统提供的气泡PopupOptions，字体的最大放大倍数为2。

气泡可以通过配置[mask](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions类型说明)来实现模态和非模态窗口，mask为true或者颜色值的时候，气泡为模态窗口，mask为false时，气泡为非模态窗口。

多个气泡同时弹出时，子窗内显示的气泡比主窗内显示的气泡层级高，所处窗口相同时，后面弹出的气泡层级比先弹出的气泡层级高。

## 文本提示气泡

文本提示气泡常用于展示带有文本的信息提示，适用于无交互的场景。Popup属性需绑定组件，当bindPopup属性的参数show为true时，会弹出气泡提示。

在Button组件上绑定Popup属性，每次点击Button按钮时，handlePopup会切换布尔值。当值为true时，触发bindPopup弹出气泡。

<!-- @[text_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/TextPrompts.ets) -->

``` TypeScript
@Entry
@Component
export struct TextPopupExample {
  @State handlePopup: boolean = false;

  build() {
    NavDestination() {
      Column({ space: 12 }) {

        Column() {
          Button('PopupOptions')
            .id('PopupOptions')
            .margin({ top: 300 })
            .onClick(() => {
              this.handlePopup = !this.handlePopup;
            })
            .bindPopup(this.handlePopup, {
              message: 'This is a popup with PopupOptions',
            })
        }.width('100%').padding({ top: 5 })

      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    // ···
  }
}
```

![zh-cn_image_0000001511740524](figures/zh-cn_image_0000001511740524.png)

## 添加气泡状态变化的事件

通过onStateChange参数为气泡添加状态变化的事件回调，可以判断气泡的当前显示状态。

<!-- @[state_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/PopupStateChange.ets) -->

![PopupOnStateChange](figures/PopupOnStateChange.gif)

## 带按钮的提示气泡

通过primaryButton、secondaryButton属性为气泡最多设置两个Button按钮，通过此按钮进行简单的交互，开发者可以通过配置action参数来设置想要触发的操作。

<!-- @[button_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/ButtonPopup.ets) -->

![zh-cn_other_0000001500740342](figures/zh-cn_other_0000001500740342.jpeg)

## 气泡的动画

通过定义transition，可以控制气泡的进场和出场动画效果。

<!-- @[animation_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/PopupAnimation.ets) -->

![popup_transition](figures/popup_transition.gif)

## 自定义气泡

开发者可以使用CustomPopupOptions的builder创建自定义气泡，\@Builder中可以放自定义的内容。除此之外，还可以通过popupColor等参数控制气泡样式。

<!-- @[custom_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/CustomPopup.ets) -->

使用者通过配置placement参数将弹出的气泡放到需要提示的位置。弹窗构造器会触发弹出提示信息，来引导使用者完成操作，也让使用者有更好的UI体验。

![zh-cn_other_0000001500900234](figures/zh-cn_other_0000001500900234.jpeg)

## 气泡样式

气泡除了可以通过builder实现自定义气泡，还可以通过接口设置气泡的样式和显示效果。

背景颜色：气泡的背景色默认为透明，但是会有一个默认的模糊效果，手机上为COMPONENT\_ULTRA\_THICK。
蒙层样式：气泡默认有蒙层，且蒙层的颜色为透明。
显示大小：气泡大小由内部的builder大小或者message的长度决定的。
显示位置：气泡默认显示在宿主组件的下方，可以通过Placement接口来配置其显示位置以及对齐方向。
以下示例通过设置popupColor（背景颜色）、mask（蒙层样式）、width（气泡宽度）、placement（显示位置）实现气泡的样式。

<!-- @[style_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/PopupStyle.ets) -->

![image](figures/UIpopupStyle.gif)

## 气泡避让软键盘

当软键盘弹出时，气泡默认不会对其避让，可能导致气泡被软键盘覆盖，这时需要设置keyboardAvoidMode为KeyboardAvoidMode.DEFAULT，来使气泡避让键盘。这时如果当前没有位置放下气泡时，气泡会从预设位置平移覆盖宿主组件。

<!-- @[avoidSoftKeyboard_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/PopupAvoidSoftKeyboard.ets) -->

![image](figures/avoidKeyboard.gif)


## 设置气泡内的多态效果

目前使用@Builder自定义气泡内容时，默认不支持多态样式，可以使用@Component新建一个组件实现按下气泡中的内容时背景变色。

<!-- @[polymorphicEffect_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/PopupPolymorphicEffect.ets) -->

![popupStateStyle](figures/popupStateStyle.gif)

## 气泡支持避让中轴

从API version 18起，气泡支持中轴避让功能。从API version 20开始，在2in1设备上默认启用（仅在窗口处于瀑布模式时产生避让）。开发者可通过[PopupOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#popupoptions类型说明)中的enableHoverMode属性，控制气泡是否启用中轴避让。

> **说明：** 
> - 如果气泡的点击位置在中轴区域，则气泡不会避让。
> - 2in1设备上需同时满足窗口处于瀑布模式才会产生避让。

<!-- @[supportedAvoidAxis_popup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/popup/PopupSupportedAvoidAxis.ets) -->