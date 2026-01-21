# stateStyles: Applying Polymorphic Styles
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @zhang_yixin13-->


Unlike \@Styles, which are used to reuse styles only on static pages, stateStyles enables you to set dynamic, state-specific styles. This topic explores the implementation of polymorphic styles through stateStyles.

> **NOTE**
>
> Polymorphic styles support only universal attributes. If a polymorphic style does not take effect, the attribute may be a private, component-specific attribute, for example, [fontColor](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-text-style.md) or [backgroundColor](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md) of the [TextInput](../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md) component. In this case, you can use [attributeModifier](../../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier) to dynamically set component attributes to enable the polymorphic style.

## Overview

stateStyles is an attribute method that sets the style based on the internal state of a component. It is similar to a CSS pseudo-class, with different syntax. ArkUI provides the following states:

- focused

- normal

- pressed

- disabled

- clicked

- selected<sup>10+</sup>

> **NOTE**
>
> Currently, the focused state can be triggered only by pressing the **Tab** or arrow keys on an external keyboard. Triggering through key presses in nested scrollable components is not supported.


## Use Scenarios


### Common Scenarios

This example shows the most basic application scenario of stateStyles. **Button1** is the first component and **Button2** the second component. When either of these components is pressed, the black style specified for **pressed** takes effect. When the **Tab** key is pressed for sequential navigation, **Button1** obtains focus and is displayed in the pink style specified for **focused**. When **Button 2** is focused, it is displayed in the pink style specified for **focused**, and **Button1** changes to the blue style specified for **normal**.

<!-- @[state_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateStyle/entry/src/main/ets/pages/StateStyle/StateStylesSample.ets) -->

``` TypeScript
@Entry
@Component
struct StateStylesSample {
  build() {
    Column() {
      Button('Button1')
        .stateStyles({
          focused: {
            .backgroundColor('#ffffeef0')
          },
          pressed: {
            .backgroundColor('#ff707070')
          },
          normal: {
            .backgroundColor('#ff2787d9')
          }
        })
        .margin(20)
      Button('Button2')
        .stateStyles({
          focused: {
            .backgroundColor('#ffffeef0')
          },
          pressed: {
            .backgroundColor('#ff707070')
          },
          normal: {
            .backgroundColor('#ff2787d9')
          }
        })
    }.margin('30%')
  }
}
```



  **Figure 1** Focused and pressed states 

![Video_2023-03-17_120758](figures/Video_2023-03-17_120758.gif)


### Combined Use of \@Styles and stateStyles

The following example uses \@Styles to specify different states of stateStyles.


<!-- @[normal_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateStyle/entry/src/main/ets/pages/NormalStyle/MyComponent.ets) -->

``` TypeScript
@Entry
@Component
struct MyComponent {
  @Styles normalStyle() {
    .backgroundColor(Color.Gray)
  }

  @Styles pressedStyle() {
    .backgroundColor(Color.Red)
  }
  build() {
    Column() {
      Text('Text1')
        .fontSize(50)
        .fontColor(Color.White)
        .stateStyles({
          normal: this.normalStyle,
          pressed: this.pressedStyle,
        })
    }
  }
}
```

  **Figure 2** Normal and pressed states 

![Video_2023-03-17_144824](figures/Video_2023-03-17_144824.gif)


### Using Regular Variables and State Variables in stateStyles

stateStyles can use **this** to bind regular variables and state variables in a component.

<!-- @[focus_style](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/StateStyle/entry/src/main/ets/pages/FocusStyle/CompWithInlineStateStyles.ets) -->

``` TypeScript
@Entry
@Component
struct CompWithInlineStateStyles {
  @State focusedColor: Color = 0xD5D5D5;
  normalColor: Color = 0x004AAF;

  build() {
    Column() {
      Button('clickMe')
        .height(100)
        .width(100)
        .stateStyles({
          normal: {
            .backgroundColor(this.normalColor)
          },
          focused: {
            .backgroundColor(this.focusedColor)
          }
        })
        .onClick(() => {
          this.focusedColor = 0x707070;
        })
        .margin('30%')
    }
  }
}
```

By default, the button is displayed in blue in the normal state. When you press the **Tab** key for the first time, the button obtains focus and is displayed in the light gray style specified for **focused**. After a click event occurs and you press the **Tab** key again, the button obtains focus and changes to dark gray.

  **Figure 3** Change of the styles in focused state by a click 

![focus-stateStyles](figures/focus-stateStyles.gif)
