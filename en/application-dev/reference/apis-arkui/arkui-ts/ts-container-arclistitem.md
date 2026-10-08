# ArcListItem

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @wind_-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=608175d8fd85ddfce5e6f9d9b165b9d12862adb2 translatedAt=2026-08-21T02:21:09.283Z pushedAt=2026-08-21T06:52:50.866Z -->

A child component used to display items in an arc list. It must be used in conjunction with [ArcList](ts-container-arclist.md).

> **NOTE**
>
> - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
> - The parent component of this component can only be [ArcList](ts-container-arclist.md).
> - When **ArcListItem** is used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), its child components are created when **ArcListItem** is created. When it is used with [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) or [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), or directly as a child component of the [ArcList](ts-container-arclist.md) component, its child components are created when **ArcListItem** is laid out.
> - This component can be used on Phone, PC/2in1, Tablet, TV, and Wearable devices. In API version 22 and earlier, using it on Phone, PC/2in1, Tablet, and TV generates a compilation warning, but it can run normally.

## Modules to Import

> **NOTE**
>
> - **ArcListItemAttribute** is essential for configuring the **ArcListItem** component. In API version 21 and earlier, you must manually import **ArcListItemAttribute** after importing the **ArcListItem** component. Otherwise, a compilation error is reported. However, starting from API version 22, the compilation toolchain automatically imports **ArcListItemAttribute** when it detects the **ArcListItem** component, so manual import is no longer necessary.
>
> - If you manually import **ArcListItemAttribute**, DevEco Studio shows the import statement as disabled (grayed out). In API version 21 and earlier, removing this import statement causes a compilation error. But from API version 22 onward, removing it does not affect the functionality.

API version 21 and earlier:

```ts
import { ArcListItem, ArcListItemAttribute } from '@kit.ArkUI';
```

API version 22 and later:

```ts
import { ArcListItem } from '@kit.ArkUI';
```

## Child Components

This component can contain a single child component.

## APIs

ArcListItem()

Creates an item for the **ArcList** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### autoScale

autoScale(enable: Optional\<boolean>)

Sets whether to automatically scale the **ArcListItem**. When enabled, the **ArcListItem** automatically adjusts its display size based on its position in the arc list.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type              | Mandatory| Description                                       |
| ------ | ------------------ | ---- | ------------------------------------------- |
| enable | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<boolean> | Yes | Whether ArcListItem supports automatic scaling display. The value true means supported, and false means not supported.<br>Default value: true, automatic scaling display is supported. |

### swipeAction

swipeAction(options: Optional\<SwipeActionOptions>)

Sets the swipe action of the **ArcListItem**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type                                                        | Mandatory| Description                   |
| ------- | ------------------------------------------------------------ | ---- | ----------------------- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[SwipeActionOptions](ts-container-listitem.md#swipeactionoptions9)&gt; | Yes | Configuration options for the swipe-out operation of **ArcListItem**. For details, see **SwipeActionOptions**. If this parameter is not set, no swipe-out operation is configured. |

## Example

This example demonstrates the visual differences when auto-scaling is enabled or disabled for child items in an **ArcList** component.

```ts
// xxx.ets
import { LengthMetrics, CircleShape } from '@kit.ArkUI';
// Starting from API version 22, you do not need to manually import ArcListAttribute and ArcListItemAttribute. For details, refer to the Modules to Import section of the ArcList and ArcListItem reference documents.
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';

@Entry
@Component
struct ArcListItemExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  private watchSize: string = '466px'; // Default watch size: 466 x 466
  private itemSize: string = '414px' // Item width

  @Builder
  buildList() {
    Stack() {
      Column() {
      }
      .width(this.watchSize)
      .height(this.watchSize)
      .clipShape(new CircleShape({ width: '100%', height: '100%' }))
      .backgroundColor(0x707070)

      ArcList({ initialIndex: 3}) {
        ForEach(this.arr, (item: number) => {
          ArcListItem() {
            Button('' + item, { type: ButtonType.Capsule })
              .width(this.itemSize)
              .height('70px')
              .fontSize('40px')
              .backgroundColor(0x17A98D)
          }
          .autoScale(item % 3 == 0 || item % 5 == 0)
        }, (item: number) => item.toString())
      }
      .space(LengthMetrics.px(10))
      .borderRadius(this.watchSize)
    }
    .width(this.watchSize)
    .height(this.watchSize)
  }

  build() {
    Column() {
      this.buildList();
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```

![arkts-arclistitem](figures/arkts-arclistitem.png)