# \@Extend Decorator: Defining Extended Component Styles
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @BlYynNe-->
<!--Designer: @BlYynNe-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

Apart from [\@Styles](arkts-style.md) used to reuse styles, ArkUI also provides \@Extend for extending component styles.


> **NOTE**
>
> The APIs of this module are supported since API version 9.
>
> This decorator can be used in ArkTS widgets since API version 9.
>
> This decorator can be used in atomic services since API version 11.

## How to Use


### Syntax


```ts
@Extend(UIComponentName) function functionName { ... }
```


### Usage Rules

- Unlike \@Styles, \@Extend can encapsulate private attributes, private events, and globally defined methods of specific components.
  <!-- @[Extend_Global_Function_Extension_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/GlobalFunctionExtension.ets) -->
  
  ``` TypeScript
  // @Extend(Text) supports the private attribute fontColor of the Text component.
  @Extend(Text)
  function fancy() {
    .fontColor(Color.Red)
  }
  
  // superFancyText can call the predefined method fancy.
  @Extend(Text)
  function superFancyText(size: number) {
    .fontSize(size)
    .fancy()
  }
  ```

- When \@Extend is used to encapsulate the private attributes, private events, and globally defined methods of a specified component, \@Extend and \@Styles cannot be used together.
  ``` TypeScript
  @Styles
  function fancy() {
    .backgroundColor(Color.Red)
  }

  // superFancyText cannot call the predefined method fancy.
  @Extend(Text)
  function superFancyText(size: number) {
    .fontSize(size)
    .fancy()
  }
  ```

- Different from \@Styles decorated methods, the \@Extend decorated methods support passing parameters. The calling complies with the TS method calling convention.
  <!-- @[Extend_private_property_fancy_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendParameterUsage.ets) -->
  
  ``` TypeScript
  // xxx.ets
  @Extend(Text)
  function fancy(fontSize: number) {
    .fontColor(Color.Red)
    .fontSize(fontSize)
  }
  
  @Entry
  @Component
  struct FancyUse {
    build() {
      Row({ space: 10 }) {
        Text('Fancy')
          .fancy(16)
        Text('Fancy')
          .fancy(24)
      }
    }
  }
  ```

- Parameters passed into \@Extend decorated methods can be functions serving as event handlers.
  <!-- @[Extend_Function_handle_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendFunctionHandle.ets) -->
  
  ``` TypeScript
  @Extend(Text)
  function makeMeClick(onClick: () => void) {
    .backgroundColor(Color.Blue)
    .onClick(onClick)
  }
  
  @Entry
  @Component
  struct FancyUse {
    @State label: string = 'Hello World';
  
    onClickHandler() {
      this.label = 'Hello ArkUI';
    }
  
    build() {
      Row({ space: 10 }) {
        Text(`${this.label}`)
          .makeMeClick(() => {
            this.onClickHandler();
          })
      }
    }
  }
  ```

- Parameters passed into \@Extend decorated methods can also be [state variables](arkts-state-management-overview.md). Changes to these state variables cause the UI to re-render.
  <!-- @[Extend_Refresh_rendering_four](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendUIStateVariable.ets) -->
  
  ``` TypeScript
  @Extend(Text)
  function fancy(fontSize: number) {
    .fontColor(Color.Blue)
    .fontSize(fontSize)
  }
  
  @Entry
  @Component
  struct FancyUse {
    @State fontSizeValue: number = 20;
  
    build() {
      Column({ space: 10 }) {
        Text('Fancy')
          .fancy(this.fontSizeValue)
          .onClick(() => {
            this.fontSizeValue = 30;
          })
      }
      .width('100%')
    }
  }
  ```
![](figures/arkts-extend-1.gif)

## Constraints

- Unlike \@Styles, \@Extend must be defined globally, outside of any component declaration.

> **NOTE**
>
> Styles defined using \@Extend can be used only in the file where they are declared and cannot be exported to other files.
>
> For styles requiring cross-file reuse, you are advised to use [AttributeModifier](../../ui/arkts-user-defined-extension-attributeModifier.md).

**Incorrect Usage**

```ts
@Entry
@Component
struct FancyUse {
  // Incorrect. @Extend must be defined globally, outside of any component declaration.
  @Extend(Text) function fancy (fontSize: number) {
    .fontSize(fontSize)
  }

  build() {
    Row({ space: 10 }) {
      Text('Fancy')
        .fancy(16)
    }
  }
}
```

**Correct Usage**
<!-- @[Extend_Positive_Example_five](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendPositiveExample.ets) -->

``` TypeScript
// Correct usage.
@Extend(Text)
function fancy(fontSize: number) {
  .fontSize(fontSize)
}

@Entry
@Component
struct FancyUse {
  build() {
    Row({ space: 10 }) {
      Text('Fancy')
        .fancy(16)
    }
  }
}
```

- Functions decorated with @Extend can be used only in the current file and cannot be exported or called in other files.

**Incorrect Usage**

``` TypeScript
  // Incorrect usage. In the pageTwo file, do not use the @Extend decorated functions defined in another file, for example, pageOne.
  // pageOne.ets
  @Extend(Button)
  function ButtonUse() {
    .width(100)
    .buttonStyle(ButtonStyleMode.NORMAL)
  }

  @Entry
  @Component
  struct extendUseOne {
    build() {
      Row() {
        Button()
          .ButtonUse()
          .height(200)
      }
    }
  }
  
  // pageTwo.ets
  @Entry
  @Component
  struct TextUse {
    build() {
      Row() {
        Text('this is TextUse')

        Button()
          .ButtonUse() // A following compilation alarm is displayed: Property 'ButtonUse' does not exist on type 'ButtonAttribute'.
          .height(50)
      }
    }
  }
```

**Correct Usage**

``` TypeScript
  // Correct usage: In the pageTwo file, you can define an @Extend decorated function whose name does not conflict with the @Extend decorated function defined in the pageOne file.
  // pageOne.ets
  @Extend(Button)
  function ButtonUse() {
    .width(100)
    .buttonStyle(ButtonStyleMode.NORMAL)
  }

  @Entry
  @Component
  struct extendUseOne {
    build() {
      Row() {
        Button()
          .ButtonUse()
          .height(200)
      }
    }
  }
  
  // pageTwo.ets
  @Extend(Button)
  function ButtonUse2() {
    .width(200)
    .buttonStyle(ButtonStyleMode.EMPHASIZED)
  }

  @Entry
  @Component
  struct TextUse {
    build() {
      Row() {
        Text('this is TextUse')
  
        Button()
          .ButtonUse2()
          .height(50)
      }
    }
  }
```
## Use Cases

The following example declares three Text components, each of which is set with the [fontStyle](../../../application-dev/reference/apis-arkui/arkui-ts/ts-appendix-enums.md#fontstyle), [fontWeight](../../../application-dev/reference/apis-arkui/arkui-ts/ts-appendix-enums.md#fontweight), and [backgroundColor](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor) styles.
<!-- @[Extend_Usage_Scenario_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendUsageScenario.ets) -->

``` TypeScript
@Entry
@Component
struct FancyUse {
  @State label: string = 'Hello World';

  build() {
    Row({ space: 10 }) {
      Text(`${this.label}`)
        .fontStyle(FontStyle.Italic)
        .fontWeight(500)
        .backgroundColor(Color.Yellow)
      Text(`${this.label}`)
        .fontStyle(FontStyle.Italic)
        .fontWeight(600)
        .backgroundColor(Color.Pink)
      Text(`${this.label}`)
        .fontStyle(FontStyle.Italic)
        .fontWeight(700)
        .backgroundColor(Color.Orange)
    }.margin('20%')
  }
}
```
![](figures/arkts-extend-2.png)

Using \@Extend for style composition and reuse:
<!-- @[Extend_Usage_Scenario_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendUsageScenariotwo.ets) -->

``` TypeScript
@Extend(Text)
function fancyText(weightValue: number, color: Color) {
  .fontStyle(FontStyle.Italic)
  .fontWeight(weightValue)
  .backgroundColor(color)
}
```

Simplified code with the use of \@Extend:
<!-- @[Extend_Usage_Scenario_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/extend/ExtendUsageScenariotwo.ets) -->

``` TypeScript
@Entry
@Component
struct FancyUse {
  @State label: string = 'Hello World';

  build() {
    Row({ space: 10 }) {
      Text(`${this.label}`)
        .fancyText(100, Color.Blue)
      Text(`${this.label}`)
        .fancyText(200, Color.Pink)
      Text(`${this.label}`)
        .fancyText(300, Color.Orange)
    }.margin('20%')
  }
}
```
