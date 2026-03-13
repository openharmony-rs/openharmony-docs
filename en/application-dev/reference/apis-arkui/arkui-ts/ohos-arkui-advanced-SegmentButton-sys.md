# SegmentButton (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xieziang-->
<!--Designer: @youzhi92-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

**SegmentButton** is a versatile component that organizes related options into segmented buttons. It supports three variants: tab-style, capsule-style single-select, and capsule-style multi-select.

>**NOTE:**
>
>- This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
>- This component is not supported on wearables. If this component is used on a wearable, the application runs abnormally, and the exception information indicates that the API is not defined.
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

Provides initial data and custom attributes for the **SegmentButton** component.

**Decorator Type**: @Observed

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| backgroundSystemMaterial<sup>23+</sup> | [uiMaterial.Material](../arkts-apis-uimaterial-sys.md#material) | No| Yes| System material for the background of the **SegmentButton** component. Different system materials have different attributes that affect the effect.<br>This attribute does not take effect for capsule-style multi-select buttons (that is, **type** is **capsule** and **multiply** is **true**).<br>Default value: no material effect<br>**System API**: This is a system API.|

## CommonSegmentButtonOptions

Defines the customizable attributes of the **SegmentButton** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| backgroundSystemMaterial<sup>23+</sup> | [uiMaterial.Material](../arkts-apis-uimaterial-sys.md#material) | No| Yes| System material for the background of the **SegmentButton** component. Different system materials have different attributes that affect the effect.<br>This attribute does not take effect for capsule-style multi-select buttons (that is, **type** is **capsule** and **multiply** is **true**).<br>Default value: no material effect<br>**System API**: This is a system API.|


## Example

### Example 1: Setting the Background Material
This example demonstrates how to set the background to a semi-transparent material by using the **backgroundSystemMaterial** attribute.

In API version 23 and later versions, the **backgroundSystemMaterial** attribute is added to [SegmentButtonOptions](#segmentbuttonoptions) and [CommonSegmentButtonOptions](#commonsegmentbuttonoptions).

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
    // Set a semi-transparent material.
    backgroundSystemMaterial: new uiMaterial.Material({ type: uiMaterial.MaterialType.SEMI_TRANSPARENT } as uiMaterial.MaterialOptions)
  });

  @State tabSelectedIndexes: number[] = [1];

  build() {
    Stack() {
      // Background for the SegmentButton component. Replace ('app.media.pic') with the image you use.
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

