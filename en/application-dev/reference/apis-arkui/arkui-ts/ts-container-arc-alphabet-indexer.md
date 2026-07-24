# ArcAlphabetIndexer

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @Hu_ZeQi-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=fd10fbb9e5b5e2e1e561a46b9ca4925a29d1a0a3 translatedAt=2026-06-30T12:27:01.371Z pushedAt=2026-07-02T08:59:42.873Z -->

The **ArcAlphabetIndexer** is a component arranged in an arc that allows quick location by alphabetical order. It can be bound with container components to quickly locate the container display area based on logical structure, making it suitable for circular screen devices such as watches.

>  **NOTE**
>
>  - This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
>  - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1 devices, tablets, and TVs, but the component can still run properly.

## Modules to Import

>  **NOTE**
>
> - **ArcAlphabetIndexerAttribute** is a key API for configuring the attributes of the **ArcAlphabetIndexer** component. In API version 21 and earlier versions, after importing the **ArcAlphabetIndexer** component, you need to manually import **ArcAlphabetIndexerAttribute**; otherwise, a compilation error will occur. Since API version 22, the compilation toolchain automatically imports **ArcAlphabetIndexerAttribute** when it detects the import of the **ArcAlphabetIndexer** component.
>
> - If you manually import **ArcAlphabetIndexerAttribute**, DevEco Studio will display the import statement in a grayed-out state. For API version 21 and earlier, removing it will cause a compilation error; since API version 22, removing it has no impact on functionality.

API version 21 and earlier:

```ts
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

API version 22 and later:

```ts
import { ArcAlphabetIndexer } from '@kit.ArkUI';
```

## Child Components

Not supported

## APIs

ArcAlphabetIndexer(info: ArcAlphabetIndexerInitInfo)

Creates and initializes an **ArcAlphabetIndexer** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name    | Type    | Mandatory    | Description    |
| -------- | -------- | -------- | -------- |
| info     | [ArcAlphabetIndexerInitInfo](#arcalphabetindexerinitinfo) | Yes| Initialization parameters for the **ArcAlphabetIndexer** component.|

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### color

color(color: Optional&lt;ColorMetrics&gt;)

Sets the text color of the index items in the normal state.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                               |
| ------ | ------------------------------------------ | ---- | ----------------------------------- |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)&gt; | Yes  | Text color.<br>Default value: **0xFFFFFF**, displayed as white|

### selectedColor

selectedColor(color: Optional&lt;ColorMetrics&gt;)

Sets the text color of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                                     |
| ------ | ------------------------------------------ | ---- | ----------------------------------------- |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)&gt; | Yes  | Text color of the selected item.<br>Default value: **0xFFFFFF**, displayed as white|

### popupColor

popupColor(color: Optional&lt;ColorMetrics&gt;)

Sets the text color for the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                                       |
| ------ | ------------------------------------------ | ---- | ------------------------------------------- |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)&gt; | Yes  | Text color of the pop-up window.<br>Default value: **0xFFFFFF**, displayed as white|

### selectedBackgroundColor

selectedBackgroundColor(color: Optional&lt;ColorMetrics&gt;)

Sets the background color of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                                     |
| ------ | ------------------------------------------ | ---- | ----------------------------------------- |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)&gt; | Yes  | Background color of the selected item.<br>Default value: **0x1F71FF**, displayed as dark blue|

### popupBackground

popupBackground(color: Optional&lt;ColorMetrics&gt;)

Sets the background color of the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                    | Mandatory| Description                                                        |
| ------ | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| color  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)&gt; | Yes  | Background color of the pop-up window.<br>Default value: **0xD8404040**, displayed as dark gray with slight transparency|

>  **NOTE**
>
>  After configuring the popup background color with **popupBackground**, avoid applying background blur effects via [popupBackgroundBlurStyle](#popupbackgroundblurstyle).

### usePopup

usePopup(enabled: Optional&lt;boolean&gt;)

Sets whether to display the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------- | ---- | -------------------------------------- |
| enabled | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;boolean&gt; | Yes  | Whether to display the pop-up window.<br>**true**: yes; **false**: no<br>Default value: **false**|

### selectedFont

selectedFont(font: Optional&lt;Font&gt;)

Sets the font style of the selected item, including size, weight, style, and font family.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                    | Mandatory| Description                                                        |
| ------ | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| font   | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[Font](ts-types.md#font)&gt; | Yes  | Font style of the selected item.<br>Default value: {<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

### popupFont

popupFont(font: Optional&lt;Font&gt;)

Sets the font style of the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                    | Mandatory| Description                                                        |
| ------ | ------------------------ | ---- | ------------------------------------------------------------ |
| font  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[Font](ts-types.md#font)&gt; | Yes  | Font style of the pop-up window.<br>Default value:<br>{<br>size:'19.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

### font

font(font: Optional&lt;Font&gt;)

Sets the default font style for the arc alphabet indexer.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                    | Mandatory| Description                                                        |
| ------ | ------------------------ | ---- | ------------------------------------------------------------ |
| font   | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[Font](ts-types.md#font)&gt; | Yes  | Default font style of the index items.<br>Default value:<br>{<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

### itemSize

itemSize(size: Optional&lt;LengthMetrics&gt;)

Sets the size of the index item area for the arc alphabet indexer.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                      | Mandatory| Description                                                        |
| ------ | -------------------------- | ---- | ------------------------------------------------------------ |
| size  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)&gt; | Yes   | Size of the index item area on the arc alphabet indexer. The index item area is circular, so this value represents the diameter of the circle. Percentage value is not supported.<br/>Default value: 24.0 <br/>Unit: vp |

### selected

selected(index: Optional&lt;number&gt;)

Sets the index of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type  | Mandatory| Description                        |
| ------ | ------ | ---- | ---------------------------- |
| index  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;number&gt; | Yes   | Index value of the selected item. If the value exceeds the valid index range, the default value **0** is used.<br/>Default value: **0**<br/>This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).|

### autoCollapse

autoCollapse(enable: Optional&lt;boolean&gt;)

Sets whether to use the adaptive collapse mode. When there are too many index items, the component automatically adjusts the display layout of the index items based on the available display space.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | ------------------------------------------ |
| enable  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;boolean&gt; | Yes  | Whether to enable the adaptive collapse behavior for the indexer.<br>Default value: **true**.<br>**true**: Enable the adaptive collapse behavior.<br>**false**: Disable the adaptive collapse behavior.|

### popupBackgroundBlurStyle

popupBackgroundBlurStyle(style: Optional&lt;BlurStyle&gt;)

Sets the background blur style of the pop-up window. If this API is not used, the blur is disabled by default. The corresponding value is **NONE** in **BlurStyle**.

> **NOTE**
>
> After configuring the pop-up window background blur style with **popupBackgroundBlurStyle**, avoid applying background colors via [popupBackground](#popupbackground).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                        | Mandatory| Description                                                        |
| ------ | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[BlurStyle](ts-universal-attributes-background.md#blurstyle9)&gt; | Yes   | Background blur style of the pop-up window.<br/>Default value: **BlurStyle.NONE**.<br/>With this attribute set, it is not recommended to set the [popupBackground](#popupbackground) attribute. |

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onSelect

onSelect(handler: Optional&lt;OnSelectCallback&gt;)

Triggered when an index item is selected. The return value is the index of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| handler  | [Optional](ts-universal-attributes-custom-property.md#optionalt)&lt;[OnSelectCallback](#onselectcallback)&gt; | Yes   | Callback used to handle the indexer selection event. |

## ArcAlphabetIndexerInitInfo

Initialization parameters for the **ArcAlphabetIndexer** component.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | ---- | ---- | -------- |
| arrayValue | string[] | No| No| Array of alphabet index strings. It cannot be set to empty.|
| selected   | number              | No| No| Index of the initial selected item. If the value is out of range, the default value **0** is used.<br>This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).|

## OnSelectCallback

type OnSelectCallback =  (index: number) => void

Defines the callback used in [onSelect](#onselect).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name | Type   | Mandatory| Description             |
| ------ | ------ | ---- | ---------------- |
| index  | number | Yes | Index value of the selected item. |

## Example

This example demonstrates how to link an **ArcAlphabetIndexer** component with an **ArcList** component for synchronized control and navigation.

```ts
// xxx.ets
import {
  LengthMetrics,
  ColorMetrics,
  ArcList,
  ArcListItem,
  ArcListAttribute,
  ArcListItemAttribute,
  ArcAlphabetIndexer,
  ArcAlphabetIndexerAttribute
} from '@kit.ArkUI';
// Starting from API version 22, you do not need to manually import ArcListAttribute, ArcListItemAttribute, and ArcAlphabetIndexerAttribute. For details, refer to the Modules to Import section of ArcList, ArcListItem, and ArcAlphabetIndexer.

@Entry
@Component
struct ArcListAndIndexer {
  private fullValue: string[] = [
    '#', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
    'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'
  ];
  private arrName : string[] = [
    '1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20',
    '21','22','23','24','25','26','27','28','29','30','31','32','33','34','35','36','37','38',
    '39','40', '41','42',
  ];

  private scrollerForList: Scroller = new Scroller();
  @State indexerIndex: number = 0;

  private watchSize: string = '466px'; // Default watch size: 233*233
  private itemSize: number = 24;  // Default size of the index item area: 24

  build() {
    Column() {
      Row() {
        Stack() {
          ArcList({ scroller: this.scrollerForList, initialIndex: 0 }) {
            ForEach(this.arrName, (itemName: string, index: number) => {
              ArcListItem() {
                Text(itemName)
                  .width('90%')
                  .height('92px')
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(index % 2 == 0 ? 0xAFEEEE : 0x00FFFF)
                  .borderRadius(23)
              }
            })
          }
          .scrollBar(BarState.Off)
          .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
            this.indexerIndex = centerIndex;
          })
          .borderWidth(1)
          .width(this.watchSize)
          .height(this.watchSize)
          .borderRadius(this.watchSize)
          .space(LengthMetrics.px(4))

          ArcAlphabetIndexer({ arrayValue: this.fullValue, selected: 0 })
            .autoCollapse(true)
            .width(this.watchSize)
            .height(this.watchSize)
            .usePopup(false)
            .selected(this.indexerIndex)
            .onSelect((index: number) => {
              this.indexerIndex = index;
              this.scrollerForList.scrollToIndex(this.indexerIndex);
            })
            .borderWidth(1)
            .hitTestBehavior(HitTestMode.Transparent)
            .selectedColor(ColorMetrics.resourceColor(0xFFFFFF))
            .selectedBackgroundColor(ColorMetrics.resourceColor(0x1F71FF))
            .color(ColorMetrics.resourceColor(0xFFFFFF))
            .popupColor(ColorMetrics.resourceColor(0xFFFFFF))
            .popupBackground(ColorMetrics.resourceColor(0xD8404040))
            .itemSize(LengthMetrics.px(this.itemSize))
            .selectedFont({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })
            .font({
              size: '11.0fp',
              style: FontStyle.Normal,
              weight: 500,
              family: 'HarmonyOS Sans'
            })

        }.width('100%').height('100%')
      }.width('100%').height('100%')
    }
  }
}
```

![arc_alphabet_indexer_preview](figures/arc_alphabet_indexer_preview.gif)