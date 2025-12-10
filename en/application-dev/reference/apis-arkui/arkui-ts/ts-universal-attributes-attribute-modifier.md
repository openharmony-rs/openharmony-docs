# Attribute Modifier
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

With the attribute modifier, you can dynamically set component attributes, complete with the **if/else** syntax and polymorphic style.

> **NOTE**
>
> - This feature is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - Ensure that the attributes set in **attributeModifier** are different from those set in other methods. Otherwise, **attributeModifier** does not take effect when the page is refreshed.
>
> - For simple scenarios requiring conditional assignment of a single component attribute, [ternary operators](../../../ui/state-management/arkts-declarative-ui-description.md#configuring-attributes) provide a concise alternative. Example: **.width(isFullScreen ? 200 : 100)**.
>
> - **attributeModifier** supports custom components since API version 20.

## attributeModifier

attributeModifier(modifier: AttributeModifier\<T>): T

Creates an attribute modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                        | Mandatory| Description                                                                                                                            |
| -------- | -------------------------------------------- | ---- | -------------------------------------------------------------------------------------------------------------------------------- |
| modifier | [AttributeModifier\<T>](#attributemodifiert) | Yes  | Modifier for dynamically setting attributes on the current component. The **if/else** syntax is supported.<br>**modifier**: attribute modifier. You need to customize classes to implement the **AttributeModifier** API.|

**Return value**

| Type| Description|
| --- | --- |
| T | Current component.|

## AttributeModifier\<T>

You need a custom class to implement the **AttributeModifier** API.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

>  **NOTE**
>
>  In the following APIs, setting the same value or object for the same attribute of the **instance** object will not trigger an update.

### applyNormalAttribute
applyNormalAttribute?(instance: T) : void

Applies the style of a component in the normal state.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type  | Mandatory  | Description                                                                                                        |
| -------- | ------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| instance | T       | Yes    | Component attribute class, which identifies the type of component to which attributes will be applied, for example, [ButtonAttribute](ts-basic-components-button.md#attributes) for the [Button](ts-basic-components-button.md) component and [TextAttribute](ts-basic-components-text.md#attributes) for the [Text](ts-basic-components-text.md) component.|

### applyPressedAttribute
applyPressedAttribute?(instance: T) : void

Applies the style of a component in the pressed state. For implementation examples, see [Example 2: Implementing the Pressed State Effect with a Modifier](#example-2-implementing-the-pressed-state-effect-with-a-modifier) and [Example 8: Implementing the Pressed State Effect for a Custom Component with a Modifier](#example-8-implementing-the-pressed-state-effect-for-a-custom-component-with-a-modifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type  | Mandatory  | Description                                                                                                        |
| -------- | ------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| instance | T       | Yes    | Component attribute class, which identifies the type of component to which attributes will be applied, for example, [ButtonAttribute](ts-basic-components-button.md#attributes) for the [Button](ts-basic-components-button.md) component and [TextAttribute](ts-basic-components-text.md#attributes) for the [Text](ts-basic-components-text.md) component.|

### applyFocusedAttribute
applyFocusedAttribute?(instance: T) : void

Applies the style of a component in the focused state. For the implementation example, see [Example 5: Setting the Focused State Style with a Modifier](#example-5-setting-the-focused-state-style-with-a-modifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type  | Mandatory  | Description                                                                                                        |
| -------- | ------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| instance | T       | Yes    | Component attribute class, which identifies the type of component to which attributes will be applied, for example, [ButtonAttribute](ts-basic-components-button.md#attributes) for the [Button](ts-basic-components-button.md) component and [TextAttribute](ts-basic-components-text.md#attributes) for the [Text](ts-basic-components-text.md) component.|

### applyDisabledAttribute
applyDisabledAttribute?(instance: T) : void

Applies the style of a component in the disabled state. For the implementation example, see [Example 6: Setting the Disabled State Style with a Modifier](#example-6-setting-the-disabled-state-style-with-a-modifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type  | Mandatory  | Description                                                                                                        |
| -------- | ------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| instance | T       | Yes    | Component attribute class, which identifies the type of component to which attributes will be applied, for example, [ButtonAttribute](ts-basic-components-button.md#attributes) for the [Button](ts-basic-components-button.md) component and [TextAttribute](ts-basic-components-text.md#attributes) for the [Text](ts-basic-components-text.md) component.|

### applySelectedAttribute
applySelectedAttribute?(instance: T) : void

Applies the style of a component in the selected state.

In the preceding APIs, **instance** indicates the component type. You can customize these APIs and use them with the **if/else **syntax. For the implementation example, see [Example 7: Setting the Selected State Style with a Modifier](#example-7-setting-the-selected-state-style-with-a-modifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type  | Mandatory  | Description                                                                                                        |
| -------- | ------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| instance | T       | Yes    | Component attribute class, which identifies the type of component to which attributes will be applied, for example, [ButtonAttribute](ts-basic-components-button.md#attributes) for the [Button](ts-basic-components-button.md) component and [TextAttribute](ts-basic-components-text.md#attributes) for the [Text](ts-basic-components-text.md) component.|

**Value range of the instance parameter**

[AlphabetIndexerAttribute](ts-container-alphabet-indexer.md#attributes), [BadgeAttribute](ts-container-badge.md#attributes), [BlankAttribute](ts-basic-components-blank.md#attributes), [ButtonAttribute](ts-basic-components-button.md#attributes), [CalendarPickerAttribute](ts-basic-components-calendarpicker.md#attributes), [CanvasAttribute](ts-components-canvas-canvas.md#attributes), [CheckboxAttribute](ts-basic-components-checkbox.md#attributes), [CheckboxGroupAttribute](ts-basic-components-checkboxgroup.md#attributes), [CircleAttribute](ts-drawing-components-circle.md#attributes), [ColumnAttribute](ts-container-column.md#attributes), [ColumnSplitAttribute](ts-container-columnsplit.md#attributes), [ShapeAttribute](ts-drawing-components-shape.md#attributes), [CommonAttribute](ts-component-general-attributes.md), [CounterAttribute](ts-container-counter.md#attributes), [DataPanelAttribute](ts-basic-components-datapanel.md#attributes), [DatePickerAttribute](ts-basic-components-datepicker.md#attributes), [DividerAttribute](ts-basic-components-divider.md#attributes), [EllipseAttribute](ts-drawing-components-ellipse.md#attributes), [FlexAttribute](ts-container-flex.md#attributes), [FlowItemAttribute](ts-container-flowitem.md#attributes), [FormLinkAttribute](ts-container-formlink.md#attributes), [GaugeAttribute](ts-basic-components-gauge.md#attributes), [GridAttribute](ts-container-grid.md#attributes), [GridColAttribute](ts-container-gridcol.md#attributes), [ColumnAttribute](ts-container-column.md#attributes), [GridItemAttribute](ts-container-griditem.md#attributes), [GridRowAttribute](ts-container-gridrow.md#attributes), [HyperlinkAttribute](ts-container-hyperlink.md#attributes), [IndicatorComponentAttribute](ts-swiper-components-indicator.md#attributes), [ImageAttribute](ts-basic-components-image.md#attributes), [ImageAnimatorAttribute](ts-basic-components-imageanimator.md#attributes), [ImageSpanAttribute](ts-basic-components-imagespan.md#attributes), [LineAttribute](ts-drawing-components-line.md#attributes), LinearIndicatorAttribute, [ListAttribute](ts-container-list.md#attributes), [ListItemAttribute](ts-container-listitem.md#attributes), [ListItemGroupAttribute](ts-container-listitemgroup.md#attributes), [LoadingProgressAttribute](ts-basic-components-loadingprogress.md#attributes), [MarqueeAttribute](ts-basic-components-marquee.md#attributes), [MenuAttribute](ts-basic-components-menu.md#attributes), [MenuItemAttribute](ts-basic-components-menuitem.md#attributes), MenuItemGroupAttribute, [NavDestinationAttribute](ts-basic-components-navdestination.md#attributes), [NavigationAttribute](ts-basic-components-navigation.md#attributes), [NavigatorAttribute](ts-container-navigator.md#attributes), [NavRouterAttribute](ts-basic-components-navrouter.md#attributes), [PanelAttribute](ts-container-panel.md#attributes), [PathAttribute](ts-drawing-components-path.md#attributes), [PatternLockAttribute](ts-basic-components-patternlock.md#attributes), [PolygonAttribute](ts-drawing-components-polygon.md#attributes), [PolylineAttribute](ts-drawing-components-polyline.md#attributes), [ProgressAttribute](ts-basic-components-progress.md#attributes), [QRCodeAttribute](ts-basic-components-qrcode.md#attributes), [RadioAttribute](ts-basic-components-radio.md#attributes), [RatingAttribute](ts-basic-components-rating.md#attributes), [RectAttribute](ts-drawing-components-rect.md#attributes), [RefreshAttribute](ts-container-refresh.md#attributes), [RelativeContainerAttribute](ts-container-relativecontainer.md#attributes), [RichEditorAttribute](ts-basic-components-richeditor.md#attributes), [RichTextAttribute](ts-basic-components-richtext.md#attributes), [RowAttribute](ts-container-row.md#attributes), [RowSplitAttribute](ts-container-rowsplit.md#attributes), [ScrollAttribute](ts-container-scroll.md#attributes), [ScrollBarAttribute](ts-basic-components-scrollbar.md#attributes), [SearchAttribute](ts-basic-components-search.md#attributes), [SelectAttribute](ts-basic-components-select.md#attributes), [ShapeAttribute](ts-drawing-components-shape.md#attributes), [SideBarContainerAttribute](ts-container-sidebarcontainer.md#attributes), [SliderAttribute](ts-basic-components-slider.md#attributes), [SpanAttribute](ts-basic-components-span.md#attributes), [StackAttribute](ts-container-stack.md#attributes), [StepperAttribute](ts-basic-components-stepper.md#attributes), [StepperItemAttribute](ts-basic-components-stepperitem.md#attributes), [SwiperAttribute](ts-container-swiper.md#attributes), [SymbolGlyphAttribute](ts-basic-components-symbolGlyph.md#attributes), [TabContentAttribute](ts-container-tabcontent.md#attributes), [TabsAttribute](ts-container-tabs.md#attributes), [TextAttribute](ts-basic-components-text.md#attributes), [TextAreaAttribute](ts-basic-components-textarea.md#attributes), [TextClockAttribute](ts-basic-components-textclock.md#attributes), [TextInputAttribute](ts-basic-components-textinput.md#attributes), [TextPickerAttribute](ts-basic-components-textpicker.md#attributes), [TextTimerAttribute](ts-basic-components-texttimer.md#attributes), [TimePickerAttribute](ts-basic-components-timepicker.md#attributes), [ToggleAttribute](ts-basic-components-toggle.md#attributes), [VideoAttribute](ts-media-components-video.md#attributes), [WaterFlowAttribute](ts-container-waterflow.md#attributes), [XComponentAttribute](ts-basic-components-xcomponent.md#attributes), [ParticleAttribute](ts-particle-animation.md#attributes)<!--Del-->, [EffectComponentAttribute](ts-container-effectcomponent-sys.md#attributes), [FormComponentAttribute](ts-basic-components-formcomponent-sys.md#attributes), [PluginComponentAttribute](ts-basic-components-plugincomponent-sys.md#attributes), [RemoteWindowAttribute](ts-basic-components-remotewindow-sys.md#attributes), [UIExtensionComponentAttribute](../js-apis-arkui-uiExtension.md#properties)<!--DelEnd-->

**Supported attributes**

1. Attributes that accept or return a [CustomBuilder](ts-types.md#custombuilder8) are not supported.
2. Attributes that accept a [modifier](../../../ui/arkts-user-defined-modifier.md) type, such as [attributeModifier](#attributemodifier), [drawModifier](./ts-universal-attributes-draw-modifier.md), and [gestureModifier](./ts-universal-attributes-gesture-modifier.md), are not supported.
3. Attribute related to [animation](./ts-animatorproperty.md) are not supported.
4. Attributes of the [gesture](../../../ui/arkts-gesture-events-binding.md) type are not supported.
5. Attribute related to [stateStyles](./ts-universal-attributes-polymorphic-style.md) are not supported.
6. Deprecated attributes are not supported.
<!--Del-->
7. Built-in component attributes are not supported.<!--DelEnd-->

When unsupported or unimplemented attributes are used, exceptions such as "Method not implemented.", "is not callable", or "Builder is not supported." are thrown. For details about the supported modifiers, see [attributeModifier Support for Attributes and Events](../../../ui/arkts-user-defined-extension-attributeModifier.md#attributemodifier-support-for-attributes-and-events).

## Custom Modifier
Custom modifiers can be used in building components and configuring attributes since API version 12. Through the custom modifiers, you can call the attribute and style APIs of encapsulated components.

**Supported custom modifiers** 

CommonModifier, ColumnModifier, ColumnSplitModifier, RowModifier, RowSplitModifier, SideBarContainerModifier, BlankModifier, DividerModifier, GridColModifier, GridRowModifier, NavDestinationModifier, NavigatorModifier, StackModifier, NavigationModifier, NavRouterModifier, StepperItemModifier, TabsModifier, GridModifier, GridItemModifier, ListModifier, ListItemModifier, ListItemGroupModifier, ScrollModifier, SwiperModifier, WaterFlowModifier, ButtonModifier, CounterModifier, TextPickerModifier, TimePickerModifier, ToggleModifier, CalendarPickerModifier, CheckboxModifier, CheckboxGroupModifier, DatePickerModifier, RadioModifier, RatingModifier, SelectModifier, SliderModifier, PatternLockModifier, SpanModifier, RichEditorModifier, RefreshModifier, SearchModifier, TextAreaModifier, TextModifier, TextInputModifier, ImageSpanModifier, ImageAnimatorModifier, ImageModifier, VideoModifier, DataPanelModifier, GaugeModifier, LoadingProgressModifier, MarqueeModifier, ProgressModifier, QRCodeModifier, TextClockModifier, TextTimerModifier, LineModifier, PathModifier, PolygonModifier, PolylineModifier, RectModifier, ShapeModifier, AlphabetIndexerModifier, FormComponentModifier, HyperlinkModifier, MenuModifier, MenuItemModifier, PanelModifier, SymbolGlyphModifier, ParticleModifier 
**CommonModifier** can be used for unexposed components.

**Precautions**
1. When a custom modifier is applied to a component, the corresponding attribute of the component takes effect. 
2. Updating the attribute value of a custom modifier changes the corresponding attribute of the component to which the modifier is applied. The custom modifier is a base class, and the constructed object is a child class object. When using the object, use **as** to assert the type as a child class. 
3. With a custom modifier applied to two components, updating the attribute value of the custom modifier changes the corresponding attributes of both components. 
4. If attributes A and B are set through a custom modifier, and then attributes C and D are set through other means, all the four attributes take effect on the component. 
5. Custom modifiers do not support change detection of state data decorated with @State. For details, see [Example 3: Understanding Custom Modifiers Do Not Support State Data Changes)](#example-3-understanding-custom-modifiers-do-not-support-state-data-changes). 
6. If you use **attributeModifier** to set attributes multiple times, all the set attributes take effect, and those attributes that are set multiple times take effect based on the configuration sequence.  

## Example
### Example 1: Switching the Background Color with a Modifier

This example demonstrates how to switch the background color of a **Button** component by binding it to a modifier.

```ts
// xxx.ets
// Set the custom AttributeModifier of the Button component.
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  public isDark: boolean = false;

  applyNormalAttribute(instance: ButtonAttribute): void {
    if (this.isDark) {
      instance.backgroundColor(Color.Black);
    } else {
      instance.backgroundColor(Color.Red);
    }
  }
}

@Entry
@Component
struct attributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button("Button")
          .attributeModifier(this.modifier)
          .onClick(() => {
            this.modifier.isDark = !this.modifier.isDark;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![attributeModifier_ifelse](figures/attributeModifier_ifelse.gif)

### Example 2: Implementing the Pressed State Effect with a Modifier

This example demonstrates how to implement a pressed state effect for a **Button** component by binding it to a modifier. For details about how to use the attribute modifier with state management V2, see [Modifiers](../../../ui/state-management/arkts-v1-v2-migration-application-and-others.md#modifiers).

```ts
// xxx.ets
// Set the custom AttributeModifier of the Button component.
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Black);
  }

  applyPressedAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Red);
  }
}

@Entry
@Component
struct attributePressedDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button("Button")
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![attributeModifier_ifelse](figures/attributeModifier_ifelse.gif)

### Example 3: Understanding Custom Modifiers Do Not Support State Data Changes

This example shows how to set the width of a custom modifier using state data. Custom modifiers do not support observing changes in data decorated with the @State decorator. Therefore, the width does not change when the button is clicked.

```ts
import { CommonModifier } from "@kit.ArkUI";

const TEST_TAG : string = "AttributeModifier";
// Set the custom AttributeModifier for the common component attributes.
class MyModifier extends CommonModifier {
  applyNormalAttribute(instance: CommonAttribute): void {
    super.applyNormalAttribute?.(instance);
  }
}

@Component
struct MyImage1 {
  @Link modifier: CommonModifier;

  build() {
    Image($r("app.media.startIcon")).attributeModifier(this.modifier as MyModifier)
  }
}

@Entry
@Component
struct Index {
  index: number = 0;
  @State width1: number = 100;
  @State height1: number = 100;
  @State myModifier: CommonModifier = new MyModifier().width(this.width1).height(this.height1).margin(10);

  build() {
    Column() {
      Button($r("app.string.EntryAbility_label"))
        .margin(10)
        .onClick(() => {
          console.info(TEST_TAG, "onClick");
          this.index++;
          if (this.index % 2 === 1) {
            this.width1 = 10;
            console.info(TEST_TAG, "setGroup1");
          } else {
            this.height1 = 10;
            console.info(TEST_TAG, "setGroup2");
          }
        })
      MyImage1({ modifier: this.myModifier })
    }
    .width('100%')
  }
}
```
![attributeModifier2](figures/attributeModifier2.gif)

### Example 4: Combining Modifier and Custom Modifier Attributes

This example demonstrates how to set **width** and **height** through a custom modifier. When the button is clicked, [borderStyle](ts-appendix-enums.md#borderstyle) and [borderWidth](ts-universal-attributes-border.md#borderwidth) are configured, with all four attributes taking effect simultaneously.

```ts
import { CommonModifier } from "@kit.ArkUI";

const TEST_TAG: string = "AttributeModifier";

// Set the custom AttributeModifier for the common component attributes.
class MyModifier extends CommonModifier {
  applyNormalAttribute(instance: CommonAttribute): void {
    super.applyNormalAttribute?.(instance);
  }

  public setGroup1(): void {
    this.borderStyle(BorderStyle.Dotted);
    this.borderWidth(8);
  }

  public setGroup2(): void {
    this.borderStyle(BorderStyle.Dashed);
    this.borderWidth(8);
  }
}

@Component
struct MyImage1 {
  @Link modifier: CommonModifier;

  build() {
    Image($r("app.media.startIcon")).attributeModifier(this.modifier as MyModifier)
  }
}

@Entry
@Component
struct Index {
  @State myModifier: CommonModifier = new MyModifier().width(100).height(100).margin(10);
  index: number = 0;

  build() {
    Column() {
      Button($r("app.string.EntryAbility_label"))
        .margin(10)
        .onClick(() => {
          console.info(TEST_TAG, "onClick");
          this.index++;
          if (this.index % 2 === 1) {
            (this.myModifier as MyModifier).setGroup1();
            console.info(TEST_TAG, "setGroup1");
          } else {
            (this.myModifier as MyModifier).setGroup2();
            console.info(TEST_TAG, "setGroup2");
          }
        })
      MyImage1({ modifier: this.myModifier })
    }
    .width('100%')
  }
}
```
![attributeModifier](figures/attributeModifier.gif)

### Example 5: Setting the Focused State Style with a Modifier

This example demonstrates how to implement a focused state style for a **Button** component by binding it to a modifier. After **Button2** is clicked, the **Button** component displays the focused style when it has focus.

```ts
// Set the custom AttributeModifier of the Button component.
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {

  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Blue);
  }
  applyFocusedAttribute(instance: ButtonAttribute): void {
    instance.backgroundColor(Color.Green);
  }
}

@Entry
@Component
struct attributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();
  @State isDisable: boolean = true;

  build() {
    Row() {
      Column() {
        Button("Button")
          .attributeModifier(this.modifier)
          .enabled(this.isDisable)
          .id("app")
        Divider().vertical(false).strokeWidth(15).color(Color.Transparent)
        Button("Button2")
          .onClick(() => {
            this.getUIContext().getFocusController().activate(true);
            this.getUIContext().getFocusController().requestFocus("app");
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![applyFocusedAttribute](figures/applyFocusedAttribute.gif)

### Example 6: Setting the Disabled State Style with a Modifier

This example demonstrates how to implement a disabled state style for a **Button** component by binding it to a modifier. After **Button2** is clicked, the **Button** component displays the disabled style when it is disabled.

```ts
// Set the custom AttributeModifier of the Button component.
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {
  applyDisabledAttribute(instance: ButtonAttribute): void {
    instance.width(200);
  }
}

@Entry
@Component
struct attributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();
  @State isDisable: boolean = true;

  build() {
    Row() {
      Column() {
        Button("Button")
          .attributeModifier(this.modifier)
          .enabled(this.isDisable)
        Divider().vertical(false).strokeWidth(15).color(Color.Transparent)
        Button("Button2")
          .onClick(() => {
            this.isDisable = !this.isDisable;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![applyDisabledAttribute](figures/applyDisabledAttribute.gif)

### Example 7: Setting the Selected State Style with a Modifier

This example demonstrates how to implement a selected state style for a **Radio** component by binding it to a modifier.

```ts
// Set the custom AttributeModifier for the Radio component.
class MyRadioModifier implements AttributeModifier<RadioAttribute> {
  applyNormalAttribute(instance: RadioAttribute): void {
    instance.backgroundColor(Color.Blue);
  }
  applySelectedAttribute(instance: RadioAttribute): void {
    instance.backgroundColor(Color.Red);
    instance.borderWidth(2);
  }
}

@Entry
@Component
struct attributeDemo {
  @State modifier: MyRadioModifier = new MyRadioModifier();
  @State value: boolean = false;
  @State value2: boolean = false;

  build() {
    Row() {
      Column() {
        Radio({ value: 'Radio1', group: 'radioGroup1' })
          .checked(this.value)
          .height(50)
          .width(50)
          .borderWidth(0)
          .borderRadius(30)
          .onClick(() => {
            this.value = !this.value;
          })
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![applySelectedAttribute](figures/applySelectedAttribute.gif)

### Example 8: Implementing the Pressed State Effect for a Custom Component with a Modifier

This example demonstrates how to implement a pressed state effect for a custom component (**Common**) by binding it to a modifier. 

```ts
// xxx.ets
// Set the custom AttributeModifier for the custom component attribute.
class CustomModifier implements AttributeModifier<CommonAttribute> {
  applyNormalAttribute(instance: CommonAttribute): void {
    instance.backgroundColor(Color.Blue)
  }

  applyPressedAttribute(instance: CommonAttribute): void {
    instance.backgroundColor(Color.Gray)
  }
}

@Entry
@Component
struct attributePressedDemo {
  @State  modifier: CustomModifier = new CustomModifier()

  build() {
    Row() {
      Column() {
        ChildComponent()
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}

// Custom component
@Component
struct ChildComponent {
  build() {
    Text("common").fontColor(Color.White).fontSize(28).textAlign(TextAlign.Center)
      .width('35%')
      .height('10%')
  }
}
```
![attributeModifier_common](figures/attributeModifier_common.gif)
