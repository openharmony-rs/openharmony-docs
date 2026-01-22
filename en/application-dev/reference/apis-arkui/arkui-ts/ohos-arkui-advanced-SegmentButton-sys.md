# SegmentButton (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xieziang-->
<!--Designer: @youzhi92-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

The **SegmentButton** component includes tab buttons, capsule buttons for single-choice, and capsule buttons for multi-choice.

>**NOTE:**
>
>- This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
>- This component is not supported on wearables. When this component is used on a wearable device, the app runs abnormally, and the exception information indicates that the API is not defined.
>
>- This component supports only two to five buttons.
>
>- The current page contains only the system APIs of this module. For details about other public APIs, see [SegmentButton](ohos-arkui-advanced-SegmentButton.md).


## Modules to Import

```ts
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray } from '@kit.ArkUI';
```


## SegmentButtonOptions

>**NOTE**
> 
> The component does not support custom font type settings.

The **SegmentButtonOption** class provides initial data and custom attributes for the **SegmentButton** component.

**Decorator Type**: @Observed

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| backgroundSystemMaterial<sup>23+</sup> | [uiMaterial.Material](../arkts-apis-uimaterial-sys.md#material) | No| Yes| System material of the background of the SegmentButton component. Different system materials have different attributes that affect the effect.<br>This attribute does not take effect for capsule buttons for multi-choice (that is, the type is "capsule" and multiply is true).<br>Default value: no material effect<br>**System API**: This is a system API.|

## CommonSegmentButtonOptions

Defines the customizable attributes of the segmented button component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| backgroundSystemMaterial<sup>23+</sup> | [uiMaterial.Material](../arkts-apis-uimaterial-sys.md#material) | No| Yes| System material of the background board of the segmented button component. Different system materials contain different attributes that affect the effect.<br>This attribute does not take effect for capsule buttons with the multiple selection mode enabled (that is, the type is capsule and multiply is true).<br>Default value: no material effect<br>**System API**: This is a system API.|


## Example

### Example 1 (setting the background board material)
In the following example, the backgroundSystemMaterial attribute is used to set a translucent background board material for the segmented button.

In API version 23 and later versions, the backgroundSystemMaterial attribute is added to [SegmentButtonOptions](#segmentbuttonoptions) and [CommonSegmentButtonOptions](#commonsegmentbuttonoptions).

```ts
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';
import uiMaterial from '@ohos.arkui.uiMaterial';


@Entry
@Component
struct IndexCl {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab 1' }, { text: 'Tab 2' }, {
      text: 'Tab 3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundColor: Color.Transparent,
    // Set the material to be translucent.
    backgroundSystemMaterial: new uiMaterial.Material({ type: uiMaterial.MaterialType.SEMI_TRANSPARENT } as uiMaterial.MaterialOptions)
  });

  @State tabSelectedIndexes: number[] = [1];

  build() {
    Stack() {
      // Use the image as the background of the segment button. ('app.media.pic') needs to be replaced with the image required by the developer.
      Image($r('app.media.pic'))
      Column() {
        SegmentButton({
          options: this.tabOptions,
          selectedIndexes: $tabSelectedIndexes
        })
      }
    }
  }
}

```

