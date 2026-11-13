# Content Modifier
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309; @liyujie43-->
<!--Designer: @liyi0309; @weixin_52725220-->
<!--Tester: @lxl007; @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b8324c027658771f98ef8b737ea8f258c193c8ff translatedAt=2026-11-03T03:17:20.293Z pushedAt=2026-11-13T01:06:00.084Z nl=1 -->

You can apply a content modifier to a component to customize its content area using a style builder.

> **NOTE**
>
> - This feature is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## ContentModifier\<T>

You need a custom class to implement the **ContentModifier** API.

### applyContent

applyContent(): WrappedBuilder<[T]>

Builder of the custom content area.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value** 

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [WrappedBuilder\<[T]>](../../../ui/state-management/arkts-wrapBuilder.md) | Component attribute class, which is used to distinguish different information required by different components after content areas are customized, for example, **ButtonConfiguration** for the **Button** component and **CheckBoxConfiguration** of the **Checkbox** component.|

**Value range of the T parameter:**

[ButtonConfiguration](ts-basic-components-button.md#buttonconfiguration12), [CheckBoxConfiguration](ts-basic-components-checkbox.md#checkboxconfiguration12), [DataPanelConfiguration](ts-basic-components-datapanel.md#datapanelconfiguration12), [TextClockConfiguration](ts-basic-components-textclock.md#textclockconfiguration12), [ToggleConfiguration](ts-basic-components-toggle.md#toggleconfiguration12), [GaugeConfiguration](ts-basic-components-gauge.md#gaugeconfiguration12), [LoadingProgressConfiguration](ts-basic-components-loadingprogress.md#loadingprogressconfiguration12), [RadioConfiguration](ts-basic-components-radio.md#radioconfiguration12), [ProgressConfiguration](ts-basic-components-progress.md#progressconfiguration12), [RatingConfiguration](ts-basic-components-rating.md#ratingconfiguration12), [SliderConfiguration](ts-basic-components-slider.md#sliderconfiguration12)

**Supported attributes**

Supports the universal attribute [enabled](ts-universal-attributes-enable.md#enabled) and [contentModifier](#contentmodifiert).
## CommonConfiguration\<T>

You need a custom class to implement the **ContentModifier** API.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type   | Read-Only | Optional | Description             |
| ------ | ------ | ---------------- | ---------------- | ---------------- |
| enabled | boolean | No| No| Whether to enable the content modifier and respond to operations such as **triggerChange**. The value **true** means to enable the content modifier and respond to operations such as **triggerChange**, and **false** means the opposite.|
| contentModifier | [ContentModifier\<T>](#contentmodifiert) | No| No| Content modifier that sends the component information required by users to the custom content area.|


## Example

This example demonstrates how to create a custom check box using **ContentModifier**. This check box comes in the custom pentagon style instead of the original check box style. When selected, the check box shows a red triangle pattern inside, and the title displays the word "selected"; when deselected, the check box hides the red triangle pattern inside, and the title displays the word "unselected."

```ts
// xxx.ets
class MyCheckboxStyle implements ContentModifier<CheckBoxConfiguration> {
  selectedColor: Color = Color.White;

  constructor(selectedColor: Color) {
    this.selectedColor = selectedColor;
  }

  applyContent(): WrappedBuilder<[CheckBoxConfiguration]> {
    return wrapBuilder(buildCheckbox);
  }
}

@Builder
function buildCheckbox(config: CheckBoxConfiguration) {
  Column({ space: 10 }) {
    Text(config.name + (config.selected ? " (selected)" : " (not selected)"))
    Shape() {
      // Pentagon check box style
      Path()
        .width(200)
        .height(60)
        .commands('M100 0 L0 100 L50 200 L150 200 L200 100 Z')
        .fillOpacity(0)
        .strokeWidth(3)
      // Red triangle pattern style
      Path()
        .width(10)
        .height(10)
        .commands('M50 0 L100 100 L0 100 Z')
        .visibility(config.selected ? Visibility.Visible : Visibility.Hidden)
        .fill(config.selected ? (config.contentModifier as MyCheckboxStyle).selectedColor : Color.Black)
        .stroke((config.contentModifier as MyCheckboxStyle).selectedColor)
        .margin({ left: 11, top: 10 })
    }
    .width(300)
    .height(200)
    .viewPort({
      x: 0,
      y: 0,
      width: 310,
      height: 310
    })
    .strokeLineJoin(LineJoinStyle.Miter)
    .strokeMiterLimit(5)
    .onClick(() => {
      // Trigger the check box state change upon click.
      if (config.selected) {
        config.triggerChange(false);
      } else {
        config.triggerChange(true);
      }
    })
    .margin({ left: 150 })
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Checkbox({ name: 'Check box status', group: 'checkboxGroup' })
          .select(true)
          .contentModifier(new MyCheckboxStyle(Color.Red))
          .onChange((value: boolean) => {
            console.info('Checkbox change is' + value);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

![](figures/common_builder.gif)
