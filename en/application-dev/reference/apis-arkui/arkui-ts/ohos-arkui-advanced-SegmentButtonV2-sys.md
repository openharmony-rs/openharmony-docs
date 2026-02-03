# SegmentButtonV2 (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xieziang-->
<!--Designer: @youzhi92-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

**SegmentButtonV2** is a versatile component that organizes related options into visually grouped buttons. It supports three variants: tab-style, capsule-style single-select, and capsule-style multi-select.

> **NOTE:**
>
> - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The current page contains only the system APIs of this module. For details about other public APIs, see [SegmentButtonV2](ohos-arkui-advanced-SegmentButtonV2.md).

## Modules to Import

```ts
import { TabSegmentButtonV2, CapsuleSegmentButtonV2, MultiCapsuleSegmentButtonV2, SegmentButtonV2Items } from '@kit.ArkUI';
```

## TabSegmentButtonV2

Tabbed segment button.

**Decorator**: @ComponentV2

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type | Mandatory| Decorator| Description|
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| backgroundSystemMaterial<sup>23+</sup> | [uiMaterial.Material](../arkts-apis-uimaterial-sys.md#material) | No| @Param | System material of the background of the segment button component. Different system materials have different attributes that affect the effect.<br>Default value: no material effect<br>This member is read-only and cannot be modified.<br>**System API**: This is a system API.|

## CapsuleSegmentButtonV2

Capsule segment button.

**Decorator**: @ComponentV2

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type | Mandatory| Decorator| Description|
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| backgroundSystemMaterial<sup>23+</sup> | [uiMaterial.Material](../arkts-apis-uimaterial-sys.md#material)  | No| @Param | System material of the background plate of the segmented button component. Different system materials contain different attributes that affect the effect.<br>Default value: no material effect<br>This member is read-only and cannot be modified.<br>**System API**: This is a system API.|

## Example

### Example 1 (setting the background plate material)
In the following example, the backgroundSystemMaterial attribute is used to set a translucent background plate material for the segmented button.

In API version 23 and later versions, the **backgroundSystemMaterial** attribute is added to [TabSegmentButtonV2](#tabsegmentbuttonv2) and [CapsuleSegmentButtonV2](#capsulesegmentbuttonv2).

```ts
import { SegmentButtonV2Items, TabSegmentButtonV2, CapsuleSegmentButtonV2 } from '@kit.ArkUI';
import uiMaterial from '@ohos.arkui.uiMaterial';

@Entry
@ComponentV2
struct SegmentButtonV2Example {
  @Local textItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { text: 'Phone'},
    { text: 'Tablet' },
    { text: 'PC/2in1' },
    { text: 'Wearable' },
  ]);
  @Local textSelectedIndex: number = 0;

  @Local imageItems: SegmentButtonV2Items = new SegmentButtonV2Items([
    { icon: $r('sys.media.ohos_ic_public_device_phone') },
    { icon: $r('sys.media.ohos_ic_public_device_pad') },
    { icon: $r('sys.media.ohos_ic_public_device_matebook') },
    { icon: $r('sys.media.ohos_ic_public_device_watch') },
  ]);
  @Local imageSelectedIndex: number = 0;

  build() {
    Scroll() {
      Stack() {
        // Background of the segmented button. Replace 'app.media.pic' with the image required by the developer.
        Image($r('app.media.pic'))
        Column({ space: 12 }) {
          VCard({ title: 'Text Button' }) {
            TabSegmentButtonV2({
              items: this.textItems,
              selectedIndex: this.textSelectedIndex!!,
              // Set the material to be translucent.
              backgroundSystemMaterial:
              new uiMaterial.Material({ type: uiMaterial.MaterialType.SEMI_TRANSPARENT } as uiMaterial.MaterialOptions)
            })
          }

          VCard({ title: 'Icon-only option' }) {
            CapsuleSegmentButtonV2({
              items: this.imageItems,
              selectedIndex: this.imageSelectedIndex!!,
              // Set the material to be translucent.
              backgroundSystemMaterial:
              new uiMaterial.Material({ type: uiMaterial.MaterialType.SEMI_TRANSPARENT } as uiMaterial.MaterialOptions)
            })
          }

        }
        .constraintSize({ minHeight: '100%' })
        .justifyContent(FlexAlign.Start)
        .padding(16)
      }
      .backgroundColor('#f1f3f5')
      .width('100%')
      .height('100%')
    }
  }
}

@Builder
function Noop() {
}

@Component
export struct VCard {
  @Prop
  title: ResourceStr;
  @BuilderParam
  content: () => void = Noop;

  build() {
    Column({ space: 8 }) {
      if (this.title) {
        Text(this.title)
          .maxLines(1)
          .textOverflow({ overflow: TextOverflow.Ellipsis })
          .constraintSize({ maxWidth: '80%' })
      }
      this.content()
    }
    .backgroundColor(Color.Transparent)
    .borderRadius(8)
    .padding(8)
    .width('100%')
  }
}
```

