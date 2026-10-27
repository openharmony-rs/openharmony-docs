# 属性修改器 (AttributeModifier)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sunbees-->
<!--Designer: @sunbees-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述
声明式语法引入了[@Styles](../ui/state-management/arkts-style.md)和[@Extend](../ui/state-management/arkts-extend.md)两个装饰器，可以解决复用相同自定义样式的问题，但是存在以下受限场景：
- @Styles和@Extend均是编译期处理，不支持跨文件的导出复用。
- @Styles仅能支持通用属性、事件，不支持组件特有的属性。
- @Styles虽然支持在多态样式下使用，但不支持传参，无法对外开放一些属性。
- @Extend虽然能支持特定组件的私有属性、事件，但同样不支持跨文件导出复用。
- @Styles、@Extend对于属性设置，无法支持业务逻辑编写，动态决定是否设置某些属性，只能通过三元表达式对所有可能设置的属性进行全量设置，设置大量属性时效率较低。


为了解决上述问题，ArkUI引入了AttributeModifier机制，可以通过Modifier对象动态修改属性。能力对比如下：
|  能力  |  @Styles  |  @Extend  |  AttributeModifier  |
| :-----: | :-----: | :-----: | :-----: |
|  跨文件导出  |  不支持  |  不支持  |  支持  |
|  通用属性设置  |  支持  |  支持  |  支持  |
|  通用事件设置  |  支持  |  支持  |  部分支持  |
|  组件特有属性设置  |  不支持  |  支持  |  部分支持  |
|  组件特有事件设置  |  不支持  |  支持  |  部分支持  |
|  参数传递  |  不支持  |  支持  |  支持  |
|  多态样式  |  支持  |  不支持  |  支持  |
|  业务逻辑  |  不支持  |  不支持  |  支持  |

可以看出，与@Styles和@Extend相比，AttributeModifier提供了更强的能力和灵活性，且在持续完善全量的属性和事件设置能力，因此推荐优先使用AttributeModifier。

## 接口定义

  <!-- @[Common_AttributeModifier](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier01.ets) -->
  
  ``` TypeScript
  declare interface AttributeModifier<T> {
  
    applyNormalAttribute?(instance: T): void;
  
    applyPressedAttribute?(instance: T): void;
  
    applyFocusedAttribute?(instance: T): void;
  
    applyDisabledAttribute?(instance: T): void;
  
    applySelectedAttribute?(instance: T): void;
  
  }
  ```


`AttributeModifier`是一个接口，开发者需要实现其中的`applyXxxAttribute`方法来实现对应场景的属性设置。`Xxx`表示多态的场景，支持默认态（`Normal`）、按压态（`Pressed`）、焦点态（`Focused`）、禁用态（`Disabled`）、选择态（`Selected`）。`T`是组件的属性类型，开发者可以在回调中获取到属性对象，通过该对象设置属性。

  <!-- @[Common_CommonMethod](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier01.ets) -->
  
  ``` TypeScript
  declare class CommonMethod<T> {
    attributeModifier(modifier: AttributeModifier<T>): T;
  }
  ```


组件的通用方法增加了`attributeModifier`方法，支持传入自定义的Modifier。由于组件在实例化时会明确`T`的类型，所以调用该方法时，`T`必须指定为组件对应的Attribute类型，或者是`CommonAttribute`。

## 使用说明

- 组件通用方法`attributeModifier`支持传入一个实现`AttributeModifier<T>`接口的实例，`T`必须指定为组件对应的Attribute类型，或者是通用属性（CommonAttribute）。
- 在组件首次初始化或者关联的状态变量发生变化时，如果传入的实例实现了对应接口，会触发`applyNormalAttribute`。
- 回调[applyNormalAttribute](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-attributemodifier-i.md#applynormalattribute)时，会传入组件属性对象，通过该对象可以设置当前组件的属性/事件。
- 暂未支持的属性/事件，执行时会抛异常。
- 属性变化触发`applyXxxAttribute`函数时，该组件之前已设置的属性，在本次变化后未设置的属性会恢复为属性的默认值。
- 可以通过该接口使用多态样式的功能，例如如果需要在组件进入按压态时设置某些属性，就可以通过自定义实现[applyPressedAttribute](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-attributemodifier-i.md#applypressedattribute)方法完成。
- 在attributeModifier中设置的属性尽量不要与其他方法设置的属性相同，避免在页面刷新时attributeModifier不生效。
- 一个Modifier实例对象可以在多个组件上使用。
- 一个组件上多次使用`applyNormalAttribute`设置不同的Modifier实例，每次状态变量刷新均会按顺序执行这些实例的方法属性设置，同样遵循属性覆盖原则。

## 设置和修改组件属性

AttributeModifier可以分离UI与样式，支持参数传递及业务逻辑编写，并且通过状态变量触发刷新。

  <!-- @[Common_MyButtonModifier](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier01.ets) -->
  
  ``` TypeScript
  export class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
    // 可以实现一个Modifier，定义私有的成员变量，外部可动态修改
    public isDark: boolean = false
  
    // 通过构造函数，创建时传参
    constructor(dark?: boolean) {
      this.isDark = dark ?? false
    }
  
    applyNormalAttribute(instance: ButtonAttribute): void {
      // instance为Button的属性对象，可以通过instance对象对属性进行修改
      if (this.isDark) { // 支持业务逻辑的编写
        // 属性变化触发apply函数时，变化前已设置并且变化后未设置的属性会恢复为默认值
        instance.backgroundColor('#707070')
      } else {
        // 支持属性的链式调用
        instance.backgroundColor('#17A98D')
          .borderColor('#707070')
          .borderWidth(2)
      }
    }
  }
  ```

  <!-- @[main_button1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/pages/Button1.ets) -->
  
  ``` TypeScript
  
  // pages/Button1.ets
  import { MyButtonModifier } from '../Common/ButtonModifier01'
  
  @Entry
  @Component
  struct Button1 {
    // 支持用状态装饰器修饰，行为和普通的对象一致
    @State modifier: MyButtonModifier = new MyButtonModifier(true);
  
    build() {
      Row() {
        Column() {
          Button('Button')
            .attributeModifier(this.modifier)
            .onClick(() => {
              // 对象的一层属性被修改时，会触发UI刷新，重新执行applyNormalAttribute
              this.modifier.isDark = !this.modifier.isDark
            })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

  ![AttributeModifier](figures/AttributeModifier01.gif)


  <!-- @[Common_MyButtonModifier](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier01.ets) -->
  
  ``` TypeScript
  export class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
    // 可以实现一个Modifier，定义私有的成员变量，外部可动态修改
    public isDark: boolean = false
  
    // 通过构造函数，创建时传参
    constructor(dark?: boolean) {
      this.isDark = dark ?? false
    }
  
    applyNormalAttribute(instance: ButtonAttribute): void {
      // instance为Button的属性对象，可以通过instance对象对属性进行修改
      if (this.isDark) { // 支持业务逻辑的编写
        // 属性变化触发apply函数时，变化前已设置并且变化后未设置的属性会恢复为默认值
        instance.backgroundColor('#707070')
      } else {
        // 支持属性的链式调用
        instance.backgroundColor('#17A98D')
          .borderColor('#707070')
          .borderWidth(2)
      }
    }
  }
  ```
  <!-- @[main_button2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/pages/Button2.ets) -->
  
  ``` TypeScript
  
  // pages/Button2.ets
  import { MyButtonModifier } from '../Common/ButtonModifier01'
  
  @Entry
  @Component
  struct Button2 {
    @State modifier: MyButtonModifier = new MyButtonModifier(true);
  
    build() {
      Row() {
        Column() {
          // 先设置属性，后设置modifier，按钮颜色会跟随modifier的值改变
          Button('Button')
            .backgroundColor('#2787D9')
            .attributeModifier(this.modifier)
            .onClick(() => {
              this.modifier.isDark = !this.modifier.isDark
            })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

  ![AttributeModifier](figures/AttributeModifier03.gif) 

当一个组件上多次使用`applyNormalAttribute`设置不同的Modifier实例时，每次状态变量刷新均会按顺序执行这些实例的方法属性设置，遵循属性覆盖原则，即后设置的属性生效。

  <!-- @[Common_MyButtonModifier2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier02.ets) -->
  
  ``` TypeScript
  export class MyButtonModifier2 implements AttributeModifier<ButtonAttribute> {
    public isDark: boolean = false
  
    constructor(dark?: boolean) {
      this.isDark = dark ?? false
    }
  
    applyNormalAttribute(instance: ButtonAttribute): void {
      if (this.isDark) {
        instance.backgroundColor(Color.Black)
          .width(200)
      } else {
        instance.backgroundColor(Color.Red)
          .width(100)
      }
    }
  }
  ```
  <!-- @[Common_MyButtonModifier3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier03.ets) -->
  
  ``` TypeScript
  export class MyButtonModifier3 implements AttributeModifier<ButtonAttribute> {
    public isDark2: boolean = false
  
    constructor(dark?: boolean) {
      this.isDark2 = dark ? dark : false
    }
  
    applyNormalAttribute(instance: ButtonAttribute): void {
      if (this.isDark2) {
        instance.backgroundColor('#2787D9')
      } else {
        instance.backgroundColor('#707070')
      }
    }
  }
  ```
  <!-- @[main_button3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/pages/Button3.ets) -->
  
  ``` TypeScript
  
  // pages/Button3.ets
  import { MyButtonModifier2 } from '../Common/ButtonModifier02';
  import { MyButtonModifier3 } from '../Common/ButtonModifier03';
  
  @Entry
  @Component
  struct Button3 {
    @State modifier: MyButtonModifier2 = new MyButtonModifier2(true);
    @State modifier2: MyButtonModifier3 = new MyButtonModifier3(true);
  
    build() {
      Row() {
        Column() {
          Button('Button')
            .attributeModifier(this.modifier)
            .attributeModifier(this.modifier2)
            .onClick(() => {
              this.modifier.isDark = !this.modifier.isDark
              this.modifier2.isDark2 = !this.modifier2.isDark2
            })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

  ![AttributeModifier](figures/AttributeModifier04.gif) 

## 设置多态样式、事件

使用`AttributeModifier`设置多态样式、事件，实现事件逻辑的复用，支持默认态（`Normal`）、按压态（`Pressed`）、焦点态（`Focused`）、禁用态（`Disabled`）、选择态（`Selected`）。例如如果需要在组件进入按压态时设置某些属性，就可以通过自定义实现`applyPressedAttribute`方法完成。

  <!-- @[Common_MyButtonModifier4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/Common/ButtonModifier04.ets) -->
  
  ``` TypeScript
  export class MyButtonModifier4 implements AttributeModifier<ButtonAttribute> {
    applyNormalAttribute(instance: ButtonAttribute): void {
      // instance为Button的属性对象，设置正常状态下属性值
      instance.backgroundColor('#17A98D')
        .borderColor('#707070')
        .borderWidth(2)
    }
  
    applyPressedAttribute(instance: ButtonAttribute): void {
      // instance为Button的属性对象，设置按压状态下属性值
      instance.backgroundColor('#2787D9')
        .borderColor('#FFC000')
        .borderWidth(5)
    }
  }
  ```
  <!-- @[main_button4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/pages/Button4.ets) -->
  
  ``` TypeScript
  
  // pages/Button4.ets
  import { MyButtonModifier4 } from '../Common/ButtonModifier04'
  
  @Entry
  @Component
  struct Button4 {
    @State modifier: MyButtonModifier4 = new MyButtonModifier4();
  
    build() {
      Row() {
        Column() {
          Button('Button')
            .attributeModifier(this.modifier)
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```
  
  ![AttributeModifier](figures/AttributeModifier02.gif) 

  ## 属性或事件对attributeModifier的支持情况
  
  通过attributeModifier动态设置属性或事件的能力从API version 11开始支持。
  
  ### 属性或事件不支持attributeModifier的范围
  
  下表说明了当前不支持attributeModifier的属性或事件。若无特殊说明，属性或事件默认在首次开放时支持attributeModifier。
  
  | 组件通用信息/系统组件的名称 | 属性/事件的名称             | 告警信息                  | 说明                                    |
  | ------------------------ | -------- | ----------------------------------------- | ------------------------ |
  | CommonAttribute | [accessibilityText](../reference/apis-arkui/arkts-apis/arkts-arkui-accessibilityspanoptions-i.md#accessibilitytext)     | -   | -  |
  | CommonAttribute | [accessibilityDescription](../reference/apis-arkui/arkts-apis/arkts-arkui-accessibilityspanoptions-i.md#accessibilitydescription)     | -   | -  |
  | CommonAttribute | [animation](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-marqueedynamicsyncscenetype-e.md#animation)                | Method not implemented.   | 不支持animation相关属性。                 |
  | CommonAttribute | attributeModifier        | -                         | attributeModifier不支持嵌套使用，不生效。 |
  | CommonAttribute | [backgroundFilter](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundfilter)         | is not callable           | -                                         |
  | CommonAttribute | [compositingFilter](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#compositingfilter)        | is not callable           | -                                         |
  | CommonAttribute | drawModifier             | is not callable           | 不支持modifier相关的属性。                |
  | CommonAttribute | [foregroundFilter](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#foregroundfilter)         | is not callable           | -                                         |
  | CommonAttribute    | [freeze](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#freeze)                   | is not callable           | -                                         |
  | CommonAttribute    | [gesture](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-swiperdynamicsyncscenetype-e.md#gesture)                   | Method not implemented.   | 不支持gesture相关的属性。                 |
  | CommonAttribute | gestureModifier          | is not callable           | 不支持modifier相关的属性。                |
  | CommonAttribute | [onAccessibilityHover](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onaccessibilityhover)      | is not callable           | -                                         |
  | CommonAttribute | [onDigitalCrown](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondigitalcrown)            | is not callable.          | -                                       |
  | CommonAttribute | [parallelGesture](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#parallelgesture)          | Method not implemented.   | 不支持gesture相关的属性。                 |
  | CommonAttribute | [priorityGesture](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#prioritygesture)          | Method not implemented.   | 不支持gesture相关的属性。                 |
  | CommonAttribute   | [reuseId](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-statemanagement-ireusableinfo-i.md#reuseid)                  | Method not implemented.   | -                                         |
  | CommonAttribute | stateStyles              | Method not implemented.   | 不支持stateStyles相关的属性。             |
  | CommonAttribute | useSizeType            | Method not implemented.   | 不支持已废弃属性。                        |
  | CommonAttribute | visualEffect             | is not callable           | -                                         |
  | CommonAttribute | [bindContextMenu](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu) | Method not implemented. | 不支持入参为CustomBuilder。 |
  | CommonAttribute | [bindContentCover](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bindcontentcover) | Method not implemented. | 不支持入参为CustomBuilder。 |
  | CommonAttribute | [bindSheet](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bindsheet) | Method not implemented. | 不支持入参为CustomBuilder。 |
  | CommonAttribute | dragPreview | Builder is not supported. | 不支持入参为CustomBuilder。 |
  | CommonAttribute | [bindPopup](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bindpopup) | Method not implemented. | 不支持入参为CustomBuilder。 |
  | CommonAttribute | [accessibilityVirtualNode](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilityvirtualnode) | is not callable | 不支持入参为CustomBuilder。 |
  | CommonAttribute | [chainWeight](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#chainweight) | - | - |
  | CheckboxGroup |  [contentModifier](../reference/apis-arkui/arkts-components/arkts-arkui-checkboxgroup-comp-attribute.md#contentmodifier)| - | - |
  | CommonAttribute  | [backgroundImage](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-interstitialdialogaction-dialogoptions-i.md#backgroundimage) | - | - |
  | CommonAttribute  | [onClick](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonoptions-c.md#onclick) | - | - |
  | CommonAttribute  | toolbar | - | - |
  | CommonAttribute  | [accessibilityGroup](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup) | - | - |
  | CommonAttribute  | [reuse](../reference/apis-arkui/arkts-apis/arkts-arkui-buildernode-c.md#reuse) | - | - |
  | CommonAttribute  | [onGestureRecognizerJudgeBegin](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ongesturerecognizerjudgebegin) | - | - |
  | EmbeddedComponent  | [onError](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-fullscreenlaunchcomponent-fullscreenlaunchcomponent-s.md#onerror) | - | - |
  | EmbeddedComponent  | [onTerminated](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-fullscreenlaunchcomponent-fullscreenlaunchcomponent-s.md#onterminated) | - | - |
  | NavDestination | [backButtonIcon<sup>19+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#backbuttonicon) | - | - |
  | NavDestination | [menus<sup>19+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#menus) | - | - |
  | NavDestination | [customTransition](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#customtransition) | - | - |
  | Navigation | [backButtonIcon](../reference/apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#backbuttonicon) | - | - |
  | Navigation | [menus](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicenavigation-atomicservicenavigation-s.md#menus) | - | - |
  | Repeat | [each](../reference/apis-arkui/arkts-components/arkts-arkui-repeat-comp-attribute.md#each) | - | - |
  | Repeat | [key](../reference/apis-arkui/arkts-components/arkts-arkui-repeat-comp-attribute.md#key) | - | - |
  | Repeat | [virtualScroll](../reference/apis-arkui/arkts-components/arkts-arkui-repeat-comp-attribute.md#virtualscroll) | - | - |
  | Repeat | [template](../reference/apis-arkui/arkts-components/arkts-arkui-repeat-comp-attribute.md#template) | - | - |
  | Repeat | [templateId](../reference/apis-arkui/arkts-components/arkts-arkui-repeat-comp-attribute.md#templateid) | - | - |
  | Search | [customKeyboard](../reference/apis-arkui/arkts-components/arkts-arkui-search-comp-attribute.md#customkeyboard) | - | - |
  | Search | [onWillAttachIME](../reference/apis-arkui/arkts-components/arkts-arkui-search-comp-attribute.md#onwillattachime) | - | - |
  | Select | [menuItemContentModifier<sup>12+</sup>](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md#menuitemcontentmodifier) | - | - |
  | Select | [menuItemContentModifier<sup>18+</sup>](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md#menuitemcontentmodifier) | - | - |
  | Select | [textModifier](../reference/apis-arkui/arkts-components/arkts-arkui-select-comp-attribute.md#textmodifier) | - | - |
  | Select | [arrowModifier](../reference/apis-arkui/arkts-components/arkts-arkui-select-comp-attribute.md#arrowmodifier) | - | - |
  | Select | [optionTextModifier](../reference/apis-arkui/arkts-components/arkts-arkui-select-comp-attribute.md#optiontextmodifier) | - | - |
  | Select | [selectedOptionTextModifier](../reference/apis-arkui/arkts-components/arkts-arkui-select-comp-attribute.md#selectedoptiontextmodifier) | - | - |
  | Slider | [digitalCrownSensitivity](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcslider-arcslideroptions-c.md#digitalcrownsensitivity) | - | - |
  | Swiper | [prevMargin](../reference/apis-arkui/arkts-components/arkts-arkui-swiper-comp-attribute.md#prevmargin) | - | - |
  | Swiper | [nextMargin](../reference/apis-arkui/arkts-components/arkts-arkui-swiper-comp-attribute.md#nextmargin) | - | - |
  | TextArea | [customKeyboard](../reference/apis-arkui/arkts-components/arkts-arkui-textarea-comp-attribute.md#customkeyboard) | - | - |
  | Text | [bindSelectionMenu](../reference/apis-arkui/arkts-components/arkts-arkui-text-comp-attribute.md#bindselectionmenu) | - | - |
  | TextInput | [customKeyboard](../reference/apis-arkui/arkts-components/arkts-arkui-textinput-comp-attribute.md#customkeyboard) | - | - |
  | TextInput | [onWillAttachIME](../reference/apis-arkui/arkts-components/arkts-arkui-textinput-comp-attribute.md#onwillattachime) | - | - |
  | TextPicker | [onEnterSelectedArea](../reference/apis-arkui/arkts-components/arkts-arkui-textpicker-comp-attribute.md#onenterselectedarea) | - | - |
  | TimePicker | [onEnterSelectedArea](../reference/apis-arkui/arkts-components/arkts-arkui-timepicker-comp-attribute.md#onenterselectedarea) | - | - |
  
  ### 属性或事件的起始版本与支持attributeModifier版本不一致的范围
  
  下表说明了属性或事件的起始版本与默认支持attributeModifier版本不一致的情况。若无特殊说明，属性或事件默认在首次开放时支持attributeModifier。
  
  | 组件通用信息/系统组件的名称 | 属性/事件的名称                                              | 属性/事件的起始版本 | 支持attributeModifier的版本 |
  | --------------------------- | ------------------------------------------------------------ | ------------------- | --------------------------- |
  | AlphabetIndexer | [autoCollapse](../reference/apis-arkui/arkts-components/arkts-arkui-alphabetindexer-comp-attribute.md#autocollapse) | 11 | 12 |
  | Button | [buttonStyle](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md#buttonstyle) |11  |12  |
  | Button | [controlSize](../reference/apis-arkui/arkts-components/arkts-arkui-button-comp-attribute.md#controlsize) |11  |12  |
  | CalendarPicker |[onChange](../reference/apis-arkui/arkts-components/arkts-arkui-calendarpicker-comp-attribute.md#onchange)  | 18 |20  |
  | Canvas | [enableAnalyzer](../reference/apis-arkui/arkts-components/arkts-arkui-canvas-comp-attribute.md#enableanalyzer) | 12 | 20 |
  | CommonAttribute | [accessibilityTextHint](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitytexthint)    | 12   | 20|
  | CommonAttribute | [accessibilityChecked](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitychecked)     | 13 | 20  |
  | CommonAttribute | [accessibilitySelected](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilityselected)    | 13 | 20 |
  | CommonAttribute | [background](../reference/apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md#background) | 10 | 20|
  | CommonAttribute  | visualEffect | 12 | 20 |
  | CommonAttribute | [onDragStart](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondragstart) | 8 | 13 |
  | CommonAttribute  | [onVisibleAreaApproximateChange](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onvisibleareaapproximatechange) | 17     | 23     |
  | CommonAttribute  | [onVisibleAreaChange](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) | 9     | 20     |
  | CommonAttribute  | [onTouchIntercept](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ontouchintercept) | 12       | 20    |
  | CommonAttribute  | [onPreDrag](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onpredrag)    | 12                  | 20             |
  | CommonAttribute  | [onChildTouchTest](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#onchildtouchtest) | 11      | 20  |
  | CommonAttribute  | [backgroundFilter](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundfilter) | 12 | 20 |
  | CommonAttribute  | [foregroundFilter](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#foregroundfilter) | 12 | 20 |
  | CommonAttribute  | [compositingFilter](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#compositingfilter) | 12 | 20 |
  | CommonAttribute  | [foregroundBlurStyle](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#foregroundblurstyle) | 10 | 18 |
  | CommonAttribute  | [freeze<sup>12+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#freeze) | 12 | 20 |
  | CommonAttribute  | [freeze<sup>18+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#freeze) | 18 | 20 |
  | CommonAttribute  | [dragPreviewOptions](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#dragpreviewoptions) | 11 | 12 |
  | CommonAttribute  | [bindMenu](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bindmenu) | 11| 20|
  | CommonAttribute  | [transition](../reference/apis-arkui/arkts-apis/arkts-arkui-actionsheetoptions-i.md#transition) | 12| 20|
  | CommonAttribute  | [safeAreaPadding](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#safeareapadding) | 14| 18|
  | CommonAttribute  | [pixelRound](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-commonmethod-c.md#pixelround) | 11| 12|
  | ContainerSpan  | [textBackgroundStyle](../reference/apis-arkui/arkts-components/arkts-arkui-containerspan-comp-attribute.md#textbackgroundstyle) | 11 | 12 |
  | DatePicker  | [onDateChange](../reference/apis-arkui/arkts-components/arkts-arkui-datepicker-comp-attribute.md#ondatechange) | 18 | 20 |
  | FolderStack  | [alignContent](../reference/apis-arkui/arkts-components/arkts-arkui-folderstack-comp-attribute.md#aligncontent) | 11 | 12 |
  | FolderStack  | [onFolderStateChange](../reference/apis-arkui/arkts-components/arkts-arkui-folderstack-comp-attribute.md#onfolderstatechange) | 11 | 20 |
  | FolderStack  | [onHoverStatusChange](../reference/apis-arkui/arkts-components/arkts-arkui-folderstack-comp-attribute.md#onhoverstatuschange) | 11 | 20 |
  | FolderStack  | [enableAnimation](../reference/apis-arkui/arkts-components/arkts-arkui-folderstack-comp-attribute.md#enableanimation) | 11 | 12 |
  | FolderStack  | [autoHalfFold](../reference/apis-arkui/arkts-components/arkts-arkui-folderstack-comp-attribute.md#autohalffold) | 11 | 12 |
  | Gauge  | [privacySensitive](../reference/apis-arkui/arkts-components/arkts-arkui-gauge-comp-attribute.md#privacysensitive) | 12 | 20 |
  | Image  | [enableAnalyzer](../reference/apis-arkui/arkts-components/arkts-arkui-image-comp-attribute.md#enableanalyzer) | 11 | 12 |
  | Image  | [resizable](../reference/apis-arkui/arkts-apis/arkts-arkui-imageattachment-c.md#resizable) | 11 | 20 |
  | List  | OnScrollVisibleContentChangeCallback | 12 | 14 |
  | List  | [onItemDragStart](../reference/apis-arkui/arkts-components/arkts-arkui-list-comp-attribute.md#onitemdragstart) | 8 | 14 |
  | NavDestination | [title](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#title) | 9 | 12 |
  | NavDestination | [mode](../reference/apis-arkui/arkts-apis/arkts-arkui-uiobserver-navdestinationinfo-i.md#mode) | 11 | 12 |
  | NavDestination | [backButtonIcon<sup>11+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#backbuttonicon) | 11 | 12 |
  | NavDestination | [menus<sup>12+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#menus) | 12 | 14 |
  | NavDestination | [toolbarConfiguration](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#toolbarconfiguration) | 13 | 20 |
  | NavDestination | [onReady](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#onready) | 11 | 20 |
  | NavDestination | onWillAppear | 12 | 20 |
  | NavDestination | onWillDisappear | 12 | 20 |
  | NavDestination | onWillShow | 12 | 20 |
  | NavDestination | onWillHide | 12 | 20 |
  | NavDestination | [systemBarStyle](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#systembarstyle) | 12 | 20 |
  | NavDestination | [onResult](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#onresult) | 15 | 22 |
  | NavDestination | [bindToScrollable](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#bindtoscrollable) | 14 | 22 |
  | NavDestination | [bindToNestedScrollable](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#bindtonestedscrollable) | 14 | 22 |
  | NavDestination | onActive | 17 | 22 |
  | NavDestination | onInactive | 17 | 22 |
  | NavDestination | [onNewParam](../reference/apis-arkui/arkts-components/arkts-arkui-navdestination-comp-attribute.md#onnewparam) | 19 | 22 |
  | Navigation | [title](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicenavigation-atomicservicenavigation-s.md#title) | 8 | 12 |
  | Navigation | [toolbarConfiguration](../reference/apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#toolbarconfiguration) | 10 | 20 |
  | Navigation | [customNavContentTransition](../reference/apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#customnavcontenttransition) | 11 | 20 |
  | Navigation | [systemBarStyle](../reference/apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#systembarstyle) | 12 | 20 |
  | Navigation | [enableVisibilityLifecycleWithContentCover](../reference/apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#enablevisibilitylifecyclewithcontentcover) | 21 | 23 |
  | PatternLock | [backgroundColor](../reference/apis-arkui/arkts-components/arkts-arkui-patternlock-comp-attribute.md#backgroundcolor) | 9 | 20 |
  | PatternLock | [onDotConnect](../reference/apis-arkui/arkts-components/arkts-arkui-patternlock-comp-attribute.md#ondotconnect) | 11 | 20 |
  | Progress | [privacySensitive](../reference/apis-arkui/arkts-components/arkts-arkui-progress-comp-attribute.md#privacysensitive) | 12 | 20 |
  | Refresh | [onOffsetChange](../reference/apis-arkui/arkts-components/arkts-arkui-refresh-comp-attribute.md#onoffsetchange) | 12 | 20 |
  | RichEditor | [customKeyboard](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#customkeyboard) | 10 | 23 |
  | RichEditor | [onDidIMEInput](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#ondidimeinput) | 12 | 20 |
  | RichEditor | [enablePreviewText](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#enablepreviewtext) | 12 | 18 |
  | RichEditor | [placeholder](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#placeholder) | 12 | 18 |
  | RichEditor | [onWillChange](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#onwillchange) | 12 | 18 |
  | RichEditor | [onDidChange](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#ondidchange) | 12 | 18 |
  | RichEditor | [editMenuOptions](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#editmenuoptions) | 12 | 18 |
  | RichEditor | [enableKeyboardOnFocus](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#enablekeyboardonfocus) | 12 | 18 |
  | RichEditor | [enableHapticFeedback](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#enablehapticfeedback) | 13 | 20 |
  | RichEditor | [barState](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-attribute.md#barstate) | 13 | 18 |
  | Select | [menuBackgroundColor](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md#menubackgroundcolor) | 11 | 12 |
  | Select | [menuBackgroundBlurStyle](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md#menubackgroundblurstyle) | 11 | 12 |
  | Swiper | [displayCount](../reference/apis-arkui/arkts-components/arkts-arkui-swiper-comp-attribute.md#displaycount) | 8 | 12 |
  | SymbolGlyph | [fontSize](../reference/apis-arkui/arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#fontsize) | 11 | 12 |
  | SymbolGlyph | [fontColor](../reference/apis-arkui/arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#fontcolor) | 11 | 12 |
  | SymbolGlyph | [fontWeight](../reference/apis-arkui/arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#fontweight) | 11 | 12 |
  | SymbolGlyph | [effectStrategy](../reference/apis-arkui/arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) | 11 | 12 |
  | SymbolGlyph | [renderingStrategy](../reference/apis-arkui/arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#renderingstrategy) | 11 | 12 |
  | SymbolSpan | [fontSize](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md#fontsize) | 11 | 12 |
  | SymbolSpan | [fontColor](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md#fontcolor) | 11 | 12 |
  | SymbolSpan | [fontWeight](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md#fontweight) | 11 | 12 |
  | SymbolSpan | [effectStrategy](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md#effectstrategy) | 11 | 12 |
  | SymbolSpan | [renderingStrategy](../reference/apis-arkui/arkts-components/arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md#renderingstrategy) | 11 | 12 |
  | ScrollableCommonAttribute | [onWillScroll](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-scrollablecommonmethod-c.md#onwillscroll) | 12 | 14 |
  | ScrollableCommonAttribute | [onDidScroll](../reference/apis-arkui/arkts-components/arkts-arkui-common-comp-scrollablecommonmethod-c.md#ondidscroll) | 12 | 14 |
  | TabContent | [onWillShow](../reference/apis-arkui/arkts-components/arkts-arkui-tabcontent-comp-attribute.md#onwillshow) | 12 | 20 |
  | TabContent | [onWillHide](../reference/apis-arkui/arkts-components/arkts-arkui-tabcontent-comp-attribute.md#onwillhide) | 12 | 20 |
  | Tabs | [edgeEffect](../reference/apis-arkui/arkts-components/arkts-arkui-tabs-comp-attribute.md#edgeeffect) | 12 | 17 |
  | Tabs | [customContentTransition](../reference/apis-arkui/arkts-components/arkts-arkui-tabs-comp-attribute.md#customcontenttransition) | 11 | 20 |
  | Tabs | [onContentWillChange](../reference/apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicetabs-atomicservicetabs-s.md#oncontentwillchange) | 12 | 20 |
  | Tabs | [barBackgroundBlurStyle](../reference/apis-arkui/arkts-components/arkts-arkui-tabs-comp-attribute.md#barbackgroundblurstyle) | 11 | 12 |
  | TextArea | [enterKeyType](../reference/apis-arkui/arkts-components/arkts-arkui-textarea-comp-attribute.md#enterkeytype) | 11 | 12 |
  | Text | [enableHapticFeedback](../reference/apis-arkui/arkts-components/arkts-arkui-text-comp-attribute.md#enablehapticfeedback) | 13 | 18 |
  | TextInput | [showCounter](../reference/apis-arkui/arkts-components/arkts-arkui-textinput-comp-attribute.md#showcounter) | 11 | 12 |
  | TextInput | [onSecurityStateChange](../reference/apis-arkui/arkts-components/arkts-arkui-textinput-comp-attribute.md#onsecuritystatechange) | 12 | 20 |
  | TextPicker | [onScrollStop<sup>14+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-textpicker-comp-attribute.md#onscrollstop) | 14 | 20 |
  | TextPicker | [onScrollStop<sup>18+</sup>](../reference/apis-arkui/arkts-components/arkts-arkui-textpicker-comp-attribute.md#onscrollstop) | 18 | 20 |
  | TextTimer | [textShadow](../reference/apis-arkui/arkts-components/arkts-arkui-texttimer-comp-attribute.md#textshadow) | 11 | 12 |
  | TimePicker | [enableHapticFeedback](../reference/apis-arkui/arkts-components/arkts-arkui-timepicker-comp-attribute.md#enablehapticfeedback) | 12 | 18 |
  | TimePicker | [onChange](../reference/apis-arkui/arkts-components/arkts-arkui-timepicker-comp-attribute.md#onchange) | 18 | 20 |
  | Video | [enableAnalyzer](../reference/apis-arkui/arkts-components/arkts-arkui-video-comp-attribute.md#enableanalyzer) | 12 | 20 |
  | Video | [analyzerConfig](../reference/apis-arkui/arkts-components/arkts-arkui-video-comp-attribute.md#analyzerconfig) | 12 | 20 |
  | Video | [onError](../reference/apis-arkui/arkts-components/arkts-arkui-video-comp-attribute.md#onerror) | 7 | 20 |
  | WaterFlow | [onScrollIndex](../reference/apis-arkui/arkts-components/arkts-arkui-waterflow-comp-attribute.md#onscrollindex) | 11 | 20 |