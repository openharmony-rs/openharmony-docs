# ArcAlphabetIndexer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **ArcAlphabetIndexer** component is an arc-shaped component designed for quick navigation through alphabetically sorted items. It can be integrated with container components to quickly locate items within the visible area.

>  **NOTE**
>
>  This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.


## Modules to Import

> **NOTE**
>
> - **ArcAlphabetIndexerAttribute** is essential for configuring the **ArcAlphabetIndexer** component. In API version 21 and earlier, you must manually import **ArcAlphabetIndexerAttribute** after importing the **ArcAlphabetIndexer** component. Otherwise, a compilation error is reported. However, starting from API version 22, the compilation toolchain automatically imports **ArcAlphabetIndexerAttribute** when it detects the **ArcAlphabetIndexer** component, so manual import is no longer necessary.
>
> - If you manually import **ArcAlphabetIndexerAttribute**, DevEco Studio shows it as disabled (grayed out). In API version 21 and earlier, removing this import causes a compilation error. But from API version 22 onward, removing it does not affect the functionality.

API version 21 and earlier:

```
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

API version 22 and later:

```
import { ArcAlphabetIndexer } from '@kit.ArkUI';
```


## Child Components

Not supported


## APIs

ArcAlphabetIndexer(info: ArcAlphabetIndexerInitInfo)

Creates an instance of the **ArcAlphabetIndexer** component with initialization parameters.

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
| color  | [Optional&lt;ColorMetrics&gt;](../js-apis-arkui-graphics.md#colormetrics12) | Yes  | Text color.<br>Default value: **0xFFFFFF**|

### selectedColor

selectedColor(color: Optional&lt;ColorMetrics&gt;)

Sets the text color of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                                     |
| ------ | ------------------------------------------ | ---- | ----------------------------------------- |
| color  | [Optional&lt;ColorMetrics&gt;](../js-apis-arkui-graphics.md#colormetrics12) | Yes  | Text color of the selected item.<br>Default value: **0xFFFFFF**|

### popupColor

popupColor(color: Optional&lt;ColorMetrics&gt;)

Sets the text color for the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                                       |
| ------ | ------------------------------------------ | ---- | ------------------------------------------- |
| color  | [Optional&lt;ColorMetrics&gt;](../js-apis-arkui-graphics.md#colormetrics12) | Yes  | Text color of the pop-up window.<br>Default value: **0xFFFFFF**|

### selectedBackgroundColor

selectedBackgroundColor(color: Optional&lt;ColorMetrics&gt;)

Sets the background color of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                      | Mandatory| Description                                     |
| ------ | ------------------------------------------ | ---- | ----------------------------------------- |
| color  | [Optional&lt;ColorMetrics&gt;](../js-apis-arkui-graphics.md#colormetrics12) | Yes  | Background color of the selected item.<br>Default value: **0x1F71FF**|

### popupBackground

popupBackground(color: Optional&lt;ColorMetrics&gt;)

Sets the background color of the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                                    | Mandatory| Description                                                        |
| ------ | -------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| color  | [Optional&lt;ColorMetrics&gt;](../js-apis-arkui-graphics.md#colormetrics12) | Yes  | Background color of the pop-up window.<br>Default value: **0xD8404040**|

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
| enabled | Optional&lt;boolean&gt; | Yes  | Whether to display the pop-up window. **true**: display the pop-up window. **false**: Do not display the pop-up window.<br>Default value: **false**.|

### selectedFont

selectedFont(font: Optional&lt;Font&gt;)

Sets the font style of the selected item, including size, weight, style, and font family.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                    | Mandatory| Description                                                        |
| ------ | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| font   | [Optional&lt;Font&gt;](ts-types.md#font) | Yes  | Font style of the selected item.<br>Default value: {<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

### popupFont

popupFont(font: Optional&lt;Font&gt;)

Sets the font style of the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                    | Mandatory| Description                                                        |
| ------ | ------------------------ | ---- | ------------------------------------------------------------ |
| font  | [Optional&lt;Font&gt;](ts-types.md#font) | Yes  | Font style of the pop-up window.<br>Default value:<br>{<br>size:'19.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

### font

font(font: Optional&lt;Font&gt;)

Sets the default font style of the index items.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                    | Mandatory| Description                                                        |
| ------ | ------------------------ | ---- | ------------------------------------------------------------ |
| font   | [Optional&lt;Font&gt;](ts-types.md#font) | Yes  | Default font style of the index items.<br>Default value:<br>{<br>size:'13.0fp',<br> style:FontStyle.Normal,<br> weight:500,<br> family:'HarmonyOS Sans'<br>} |

### itemSize

itemSize(size: Optional&lt;LengthMetrics&gt;)

Sets the size of the index item area.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                      | Mandatory| Description                                                        |
| ------ | -------------------------- | ---- | ------------------------------------------------------------ |
| size  | [Optional&lt;LengthMetrics&gt;](../js-apis-arkui-graphics.md#lengthmetrics12) | Yes  | Size of the index item area. For the circular item area, this represents the diameter of the circle. Percentage values are not supported.<br>Default value: **24.0**<br>Unit: vp|

### selected

selected(index: Optional&lt;number&gt;)

Sets the index of the selected item.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type  | Mandatory| Description                        |
| ------ | ------ | ---- | ---------------------------- |
| index  | Optional&lt;number&gt; | Yes  | Index of the selected item.<br>Default value: **0**<br>This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md).|

### autoCollapse

autoCollapse(enable: Optional&lt;boolean&gt;)

Sets whether to enable the adaptive collapse behavior for the indexer.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type   | Mandatory| Description                                      |
| ------ | ------- | ---- | ------------------------------------------ |
| enable  | Optional&lt;boolean&gt; | Yes  | Whether to enable the adaptive collapse behavior for the indexer.<br>Default value: **true**.<br>**true**: Enable the adaptive collapse behavior.<br>**false**: Disable the adaptive collapse behavior.|

### popupBackgroundBlurStyle

popupBackgroundBlurStyle(style: Optional&lt;BlurStyle&gt;)

Sets the background blur style of the pop-up window.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Circle

**Parameters**

| Name| Type                                        | Mandatory| Description                                                        |
| ------ | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| style  | [Optional&lt;BlurStyle&gt;](ts-universal-attributes-background.md#blurstyle9) | Yes  | Background blur style of the pop-up window.<br>Preset value: **NONE**.|

>  **NOTE**
>
>  After configuring the pop-up window background blur style with **popupBackgroundBlurStyle**, avoid applying background colors via [popupBackground](#popupbackground).

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
| handler  | Optional&lt;[OnSelectCallback](#onselectcallback)&gt; | Yes  | Callback used to return the result.|


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
| index  | number | Yes| Index of the selected item.|


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

@Builder
function buildText() {
  Stack() {
    Text("head")
      .fontSize(30)
      .padding(10)
      .backgroundColor(0xF9CF93)
      .border({ width: '1px', color: Color.Black })

    Divider().width('100%').height('1px')
  }
  .alignContent(Alignment.Bottom)
}

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
          ArcList({ scroller : this.scrollerForList, initialIndex: 0 }) {
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
              size:'11.0fp',
              style:FontStyle.Normal,
              weight:500,
              family:'HarmonyOS Sans'
            })
            .font({
              size:'11.0fp',
              style:FontStyle.Normal,
              weight:500,
              family:'HarmonyOS Sans'
            })

        }.width('100%').height('100%')
      }.width('100%').height('100%')
    }
  }
}
```

![arc_alphabet_indexer_preview](figures/arc_alphabet_indexer_preview.gif)
