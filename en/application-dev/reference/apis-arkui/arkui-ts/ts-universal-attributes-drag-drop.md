# Drag and Drop Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

The component provides some attributes and APIs to configure the component's response to drag events or affect the system's handling of drag events, including whether the component can be dragged and how to customize the appearance of the drag preview.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

The ArkUI framework provides default drag and drop capabilities for the following components, allowing them to serve as the drag source (from which data can be dragged) or drop target (to which data can be dropped). You can also define drag responses by implementing common drag events.

- The following component supports drag actions by default: [Search](ts-basic-components-search.md), [TextInput](ts-basic-components-textinput.md), [TextArea](ts-basic-components-textarea.md), [RichEditor](ts-basic-components-richeditor.md), [Text](ts-basic-components-text.md), [Image](ts-basic-components-image.md), [Hyperlink](ts-container-hyperlink.md). You can control the default drag behavior by setting the [draggable](ts-universal-attributes-drag-drop.md#draggable) attribute.

- The following component supports drop actions by default: [Search](ts-basic-components-search.md), [TextInput](ts-basic-components-textinput.md), [TextArea](ts-basic-components-textarea.md), [RichEditor](ts-basic-components-richeditor.md). You can disable the default drag behavior by setting the [allowDrop](ts-universal-attributes-drag-drop.md#allowdrop) attribute to **null**.

<!--RP1--><!--RP1End-->To enable drag and drop for other components that support drag actions, set their **draggable** attribute to **true** and implement data transmission in APIs such as **onDragStart**.

> **NOTE**
>
> When using the **Text** component, set [copyOption](ts-basic-components-text.md#copyoption9) to **CopyOptions.InApp** or **CopyOptions.LocalDevice**.

## allowDrop

allowDrop(value: Array&lt;UniformDataType&gt; | null): T

Sets the type of data that can be dropped to the component. If allowDrop is not set, the component accepts all data types by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                           |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| value  | Array\<[UniformDataType](#uniformdatatype)> \| null<sup>12+</sup> | Yes  | Type of data that can be dropped to the component. Since API version 12, this parameter can be set to **null** to make the component reject all data types.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## draggable

draggable(value: boolean): T

Sets whether the component is draggable. By default, components cannot be dragged.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                          |
| ------ | ------- | ---- | ---------------------------------------------- |
| value  | boolean | Yes  | Whether the component is draggable. <br>**true**: The component is draggable.<br>**false**: The component is not draggable.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## dragPreview<sup>11+</sup>

dragPreview(value: CustomBuilder | DragItemInfo | string): T

Sets the preview image during component floating and dragging.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [CustomBuilder](ts-types.md#custombuilder8) \| [DragItemInfo](ts-universal-events-drag-drop.md#dragiteminfo) \| string<sup>12+</sup> | Yes  | Sets the preview image during component floating and dragging. This attribute is valid only when the [onDragStart](ts-universal-events-drag-drop.md#ondragstart) dragging mode is used.<br>If the component supports drag and drop and a preview is specified through [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8), that specified preview is displayed when the component is dragged. The priority of the background image returned in [onDragStart](ts-universal-events-drag-drop.md#ondragstart) is lower than that of the preview set in [dragPreview](ts-universal-attributes-drag-drop.md#dragpreview11). This means that, once set, the latter will be used in place of the former. Because [CustomBuilder](ts-types.md#custombuilder8) can be used only after offline rendering, it may increase performance overhead and latency. In light of this, you are advised to use [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) in [DragItemInfo](ts-universal-events-drag-drop.md#dragiteminfo) to set the preview.<br> When an ID of the string type is passed in, the snapshot of the component assigned the ID is used as the preview image. If the component assigned the ID cannot be found or its [Visibility](ts-appendix-enums.md#visibility) attribute is set to **None** or **Hidden**, a snapshot of the current component is used as the preview image. Currently, snapshots do not support visual effects, such as brightness, shadow, blur, and rotation.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## dragPreview<sup>15+</sup>

dragPreview(preview: CustomBuilder | DragItemInfo | string, config?: PreviewConfiguration):T

Sets the preview displayed when the component is dragged. It is used only for setting or disabling the lifting effect.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| preview  | [CustomBuilder](ts-types.md#custombuilder8) \| [DragItemInfo](ts-universal-events-drag-drop.md#dragiteminfo) \| string | Yes  | Sets the preview image during component floating and dragging. This attribute is valid only when the [onDragStart](ts-universal-events-drag-drop.md#ondragstart) dragging mode is used.<br>If the component supports drag and drop and a preview is specified through [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8), that specified preview is displayed when the component is dragged. The priority of the background image returned in [onDragStart](ts-universal-events-drag-drop.md#ondragstart) is lower than that of the preview set in [dragPreview](ts-universal-attributes-drag-drop.md#dragpreview11). This means that, once set, the latter will be used in place of the former. Because [CustomBuilder](ts-types.md#custombuilder8) can be used only after offline rendering, it may increase performance overhead and latency. In light of this, you are advised to use [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) in [DragItemInfo](ts-universal-events-drag-drop.md#dragiteminfo) to set the preview.<br> When an ID of the string type is passed in, the snapshot of the component assigned the ID is used as the preview image. If the component assigned the ID cannot be found or its [Visibility](ts-appendix-enums.md#visibility) attribute is set to **None** or **Hidden**, a snapshot of the current component is used as the preview image. Currently, snapshots do not support visual effects, such as brightness, shadow, blur, and rotation.|
| config | [PreviewConfiguration](ts-universal-events-drag-drop.md#previewconfiguration15) | No| Additional settings for the drag preview.<br>This parameter is effective only for previews set using [dragPreview](#dragpreview11).|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## dragPreviewOptions<sup>11+</sup>

dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T

Sets the preview image processing mode, number of badges, and interaction mode for preview image floating during dragging. The **onItemDragStart** dragging mode is not supported.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                           | Mandatory| Description                                                        |
| ------ | -------------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [DragPreviewOptions](#dragpreviewoptions11)<sup>11+</sup>      | Yes  | Sets the preview image processing mode and number of badges during dragging.|
| options<sup>12+</sup>| [DragInteractionOptions](#draginteractionoptions12)<sup>12+</sup>| No  | Sets the interaction mode in which the preview image floats during dragging.<br>Default value: empty|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## DragPreviewOptions<sup>11+</sup>

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | --- |
| mode | [DragPreviewMode](#dragpreviewmode11)  \|  Array<[DragPreviewMode](#dragpreviewmode11)><sup>12+</sup>| No| Yes| How the background image is processed when the component is dragged.<br>Default value: **DragPreviewMode.AUTO**<br>If **DragPreviewMode.AUTO** is along with other enum values, the setting takes precedence with **DragPreviewMode.AUTO**, and other enum values do not take effect.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| numberBadge<sup>12+</sup> | boolean  \|  number | No| Yes| Whether to display the number badge or the number displayed on the badge. For a number badge, the value range is [0, 2<sup>31</sup>-1]. Values outside this range will be processed as the default state. If the value specified is a floating-point number, only the integer part is displayed.<br>**NOTE**<br>When multiple items are dragged, use this API to set the number of items dragged.<br>Default value: **true**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| modifier<sup>12+</sup> | [ImageModifier](#imagemodifier12)| No| Yes| Style modifier to apply to the drag preview. You can use the attributes and styles supported by the image component to configure the drag preview style (see example 6). Currently, opacity, shadow, background blur, and rounded corners are supported. This parameter does not work for text dragging, which only supports the default effect.<br>1. Opacity<br>Use [opacity](ts-universal-attributes-opacity.md#opacity) to set the opacity. The value ranges from 0 to 1. If the value is set to **0** or left unspecified, it reverts to the default value **0.95**. Setting it to **1** or an invalid value makes the object completely opaque.<br>2. Shadow<br>Use the [shadow](ts-universal-attributes-image-effect.md#shadow) attribute to set the shadow.<br>3. Background blur<br>Sets the background blur effect using [backgroundEffect](ts-universal-attributes-background.md#backgroundeffect11) or [backgroundBlurStyle](ts-universal-attributes-background.md#backgroundblurstyle9). If both attributes are set, the latter setting takes effect.<br>4. Rounded corner<br>Sets the rounded corners using [border](ts-universal-attributes-border.md#border) or [borderRadius](ts-universal-attributes-border.md#borderradius). If the rounded corners are set in both mode and modifier, the rounded corners set in mode have a lower priority than those set in modifier.<br>Default value: empty, which cannot be changed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| sizeChangeEffect<sup>19+</sup> | [DraggingSizeChangeEffect](#draggingsizechangeeffect19)<sup>19+</sup> | No| Yes| Sets the transition effect between the floating image and the drag preview image.<br>Default value: DraggingSizeChangeEffect.DEFAULT<br>**Atomic service API**: This API can be used in atomic services since API version 19.|

## DragPreviewMode<sup>11+</sup>

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | ------- | -------- |
| AUTO  | 1 | Enables the system to automatically change the position of the dragged point based on the scenario and apply scaling transformations to the drag preview based on set rules.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| DISABLE_SCALE  | 2 | Disables the system's scaling behavior for the drag preview.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ENABLE_DEFAULT_SHADOW<sup>12+</sup> | 3 | Enables the default shadow effect for non-text components.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ENABLE_DEFAULT_RADIUS<sup>12+</sup> | 4 | Enables a unified rounded corner effect for non-text components, with the default value of 12 vp. If the custom rounded corner value set by the application is greater than the default value or the value set by **modifier**, the custom value is used.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ENABLE_DRAG_ITEM_GRAY_EFFECT<sup>18+</sup> | 5 | Enables the gray (transparency) effect for the original drag item, which does not apply to text content dragging. When the user starts dragging, the original item displays a gray effect. When released, the original item returns to its original appearance. After enabling the default gray effect, avoid manually modifying the opacity after dragging starts. Otherwise, the gray effect will be overridden, and the original opacity will not be correctly restored when dragging ends.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| ENABLE_MULTI_TILE_EFFECT<sup>18+</sup> | 6 | Enables the effect that multiple selected objects are not gathered when dragged by the mouse. Each dragged image is displayed in the relative position of the original position. This parameter takes effect only when multiple objects are selected and isMultiSelectionEnabled is set to true. The non-clustering effect has a higher priority than [dragPreview](#dragpreview11). This setting does not support secondary dragging, rounded corners, or scaling.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW<sup>19+</sup> | 7 | Enables the function of calculating the touch point position based on the initial size of the drag preview image. This function is used when the long-pressed floating image is different from the dragged image. Mouse drag. This parameter does not take effect when DragPreviewMode.ENABLE_MULTI_TILE_EFFECT is set.<br>**Atomic service API**: This API can be used in atomic services since API version 19.|

## DraggingSizeChangeEffect<sup>19+</sup>

When both long-press pop-up preview (see [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu12)) and drag are set on a node, this field is used to set the transition animation mode of the long-press pop-up preview and drag preview.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | ------- | -------- |
| DEFAULT | 0 | When drag is initiated, the preview image is directly switched from the menu preview image to the drag preview image of the final size.|
| SIZE_TRANSITION | 1 | When drag is initiated, the preview image is directly switched from the menu preview image to the drag preview image. The size gradually changes from the menu preview image size to the final preview image size. If the DISABLE_SCALE value in [DragPreviewMode](#dragpreviewmode11) is set, the size transition does not take effect. This is used when the long-press pop-up preview image is the same as the drag preview image.|
| SIZE_CONTENT_TRANSITION | 2 | When drag is initiated, the preview image is gradually switched to the final drag preview image. If DISABLE_SCALE in [DragPreviewMode](#dragpreviewmode11) is set, the size transition does not take effect. This is often used when the menu preview image is greatly different from the drag preview image. The transition effect includes the content transparency and size change.|


## DragInteractionOptions<sup>12+</sup>

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | ---- |
| isMultiSelectionEnabled | boolean | No| Yes| Whether to enable multiselect for the drag preview. <br>**true**: Enable multiselect for the drag preview.<br>**false**: Disable multiselect for the drag preview.<br> This parameter takes effect only for the [grid items](ts-container-griditem.md) and [list items](ts-container-listitem.md) in the [Grid](ts-container-grid.md) and [List](ts-container-list.md) containers.<br>When multiselect is enabled for an item, the child components of the item cannot be dragged. The priority levels of drag previews for multiselect, from high to low, are as follows: preview specified through a string value in [dragPreview](#dragpreview11), preview specified through **PixelMap** in **dragPreview**, and component snapshot. The Builder format in **dragPreview** is not supported.<br>The context menu bound to the component through [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu12) cannot contain the **isShown** parameter.<br>Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| defaultAnimationBeforeLifting | boolean | No| Yes| Whether to enable the default pressed state animation (compressing in size) of the component before a lift animation starts. <br>**true**: Enable the default pressed state animation.<br>**false**: Disable the default pressed state animation.<br>Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| isLiftingDisabled<sup>15+</sup> | boolean | No| Yes| Whether to disable the lifting effect during dragging. <br>**true**: Disable the lifting effect during dragging.<br>**false**: Enable the lifting effect during dragging.<br>With the value **true**, only the custom menu preview (set using [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8)), also known as the long-press preview, is displayed if both the long-press preview and drag preview are configured.<br>Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 15.|
| enableEdgeAutoScroll<sup>18+</sup> | boolean | No| Yes| Whether to trigger automatic scrolling for dragging to the edge of a scrollable component. <br>**true**: Trigger automatic scrolling.<br>**false**: Do not trigger automatic scrolling.<br>Default value: **true**<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| enableHapticFeedback<sup>18+</sup> | boolean | No| Yes| Whether to enable haptic feedback during dragging. <br>**true**: Enable haptic feedback during dragging.<br>**false**: Disable haptic feedback during dragging. This parameter takes effect only in preview scenarios with a mask (using [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu12)).<br>**NOTE**<br>The settings take effect only when the application has the ohos.permission.VIBRATE permission and the user has enabled haptic feedback.<br>Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## UniformDataType

type UniformDataType = UniformDataType

Standardized data type.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type| Description|
| ----- | ----------------- |
| [UniformDataType](../../apis-arkdata/js-apis-data-uniformTypeDescriptor.md#uniformdatatype) | Standardized data type.|

## ImageModifier<sup>12+</sup>

type ImageModifier = ImageModifier

Modifier object of the image component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type| Description|
| ----- | ----------------- |
| [ImageModifier](ts-universal-attributes-attribute-modifier.md) | Modifier object of the image component.|

## Example
### Example 1: Allowing Drag and Drop

In example 1, allowDrop is used to set whether the component can be dropped, and draggable is used to set whether the component can be dragged.

```ts
// xxx.ets
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';

@Entry
@Component
struct ImageExample {
  @State uri: string = "";
  @State aBlockArr: string[] = [];
  @State bBlockArr: string[] = [];
  @State AVisible: Visibility = Visibility.Visible;
  @State dragSuccess :Boolean = false;

  build() {
    Column() {
      Text('Image drag and drop')
        .fontSize('30dp')
      Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceAround }) {
        Image($r('app.media.icon'))
          .width(100)
          .height(100)
          .border({ width: 1 })
          .visibility(this.AVisible)
          .draggable(true)
          .onDragEnd((event: DragEvent) => {
            let ret = event.getResult();
            if(ret == 0) {
              console.info("enter ret == 0")
              this.AVisible = Visibility.Hidden;
            } else {
              console.info("enter ret != 0")
              this.AVisible = Visibility.Visible;
            }
          })
      }
      .margin({ bottom: 20 })
      Row() {
        Column(){
          Text('Invalid drop target')
            .fontSize('15dp')
            .height('10%')
          List(){
            ForEach(this.aBlockArr, (item:string, index) => {
              ListItem() {
                Image(item)
                  .width(100)
                  .height(100)
                  .border({width: 1})
              }
              .margin({ left: 30 , top : 30})
            }, (item:string) => item)
          }
          .height('90%')
          .width('100%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.TEXT])
          .onDrop((event?: DragEvent, extraParams?: string) => {
            this.uri = JSON.parse(extraParams as string)?.extraInfo;
            this.aBlockArr.splice(JSON.parse(extraParams as string)?.insertIndex, 0, this.uri);
            console.info("ondrop not udmf data");
          })
          .border({width: 1})
        }
        .height("50%")
        .width("45%")
        .border({ width: 1 })
        .margin({ left: 12 })
        Column(){
          Text('Valid drop target')
            .fontSize('15dp')
            .height('10%')
          List(){
            ForEach(this.bBlockArr, (item:string, index) => {
              ListItem() {
                Image(item)
                  .width(100)
                  .height(100)
                  .border({width: 1})
              }
              .margin({ left: 30 , top : 30})
            }, (item:string) => item)
          }
          .border({width: 1})
          .height('90%')
          .width('100%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((event?: DragEvent, extraParams?: string) => {
            console.info("enter onDrop")
            let dragData:UnifiedData = (event as DragEvent).getData() as UnifiedData;
            if(dragData != undefined) {
              let arr:Array<unifiedDataChannel.UnifiedRecord> = dragData.getRecords();
              if(arr.length > 0) {
                let image = arr[0] as unifiedDataChannel.Image;
                this.uri = image.imageUri;
                this.bBlockArr.splice(JSON.parse(extraParams as string)?.insertIndex, 0, this.uri);
              } else {
                console.info(`dragData arr is null`)
              }
            } else {
              console.info(`dragData  is undefined`)
            }
            console.info("ondrop udmf data");
            this.dragSuccess = true
          })
        }
        .height("50%")
        .width("45%")
        .border({ width: 1 })
        .margin({ left: 12 })
      }
    }.width('100%')
  }
}
```

![dragImage.gif](figures/dragImage.gif)

### Example 2: Setting the Drag Preview

Example 2: Configure dragPreview to set the preview image during drag.

```ts
// xxx.ets
@Entry
@Component
struct DragPreviewDemo{
  @Builder dragPreviewBuilder() {
    Column() {
      Text("dragPreview")
        .width(150)
        .height(50)
        .fontSize(20)
        .borderRadius(10)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
    }
  }

  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text("menu item 1")
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
      Divider()
        .height(5)
      Text("menu item 2")
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
    }
    .width(100)
  }

  build() {
    Row() {
      Column() {
        Image('/resource/image.jpeg')
          .width("30%")
          .draggable(true)
          .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
          .onDragStart(() => {
            console.info("Image onDragStart")
          })
          .dragPreview(this.dragPreviewBuilder)
      }
      .width("100%")
    }
    .height("100%")
  }
}
```

![dragPreview.gif](figures/dragPreview.gif)

### Example 3: Setting the Drag Preview Style

In example 3, dragPreviewOptions is set to ENABLE_DEFAULT_SHADOW, ENABLE_DEFAULT_RADIUS, and ENABLE_DRAG_ITEM_GRAY_EFFECT to set the default shadow, unified rounded corner effect, and gray effect.

```ts
// xxx.ets
@Entry
@Component
struct dragPreviewOptionsDemo{
  build() {
    Row() {
      Column() {
        Image('/resource/image.jpeg')
          .margin({ top: 10 })
          .width("30%")
          .draggable(true)
          .dragPreviewOptions({ mode: DragPreviewMode.AUTO })
        Image('/resource/image.jpeg')
          .margin({ top: 10 })
          .width("30%")
          .border({ radius: { topLeft: 1, topRight: 2, bottomLeft: 4, bottomRight: 8 } })
          .draggable(true)
          .onDragStart(() => {
            console.info("Image onDragStart")
          })
          .dragPreviewOptions({ mode: [ DragPreviewMode.ENABLE_DEFAULT_SHADOW, DragPreviewMode.ENABLE_DEFAULT_RADIUS, DragPreviewMode.ENABLE_DRAG_ITEM_GRAY_EFFECT ] })
      }
      .width("100%")
      .height("100%")
    }
  }
}
```

![dragPreviewMode.gif](figures/dragPreviewMode.gif)


### Example 4: Enabling Multiselect for Dragging

Example 4 shows how to configure isMultiSelectionEnabled to implement the multi-selection drag effect of the Grid component.

```ts
@Entry
@Component
struct Example {
  @State numbers: number[] = [0, 1, 2, 3, 4 , 5, 6, 7, 8]
  build() {
    Column({ space: 5}) {
      Grid() {
        ForEach(this.numbers, (item: number) => {
          GridItem() {
            Column()
              .backgroundColor(Color.Blue)
              .width('100%')
              .height('100%')
          }
          .width(90)
          .height(90)
          .selectable(true)
          .selected(true)
          .dragPreviewOptions({}, {isMultiSelectionEnabled:true})
          .onDragStart(()=>{

          })
    }, (item: string) => item)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr')
      .height(300)
    }
    .width('100%')
  }
}
```

![isMultiSelectionEnabled.gif](figures/isMultiSelectionEnabled.gif)

### Example 5: Enabling the Default Pressed State Animation

Example 5 shows how to configure defaultAnimationBeforeLifting to implement the default tap effect of the Grid component.

```ts
@Entry
@Component
struct Example {
  @State numbers: number[] = [0, 1, 2, 3, 4 , 5, 6, 7, 8]
  build() {
    Column({ space: 5}) {
      Grid() {
        ForEach(this.numbers, (item: number) => {
          GridItem() {
            Column()
              .backgroundColor(Color.Blue)
              .width('100%')
              .height('100%')
          }
          .width(90)
          .height(90)
          .selectable(true)
          .selected(true)
          .dragPreviewOptions({}, {isMultiSelectionEnabled:true, defaultAnimationBeforeLifting:true})
          .onDragStart(()=>{

          })
    }, (item: string) => item)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr')
      .height(300)
    }
    .width('100%')
  }
}
```

![defaultAnimationBeforeLifting.gif](figures/defaultAnimationBeforeLifting.gif)

### Example 6: Customizing the Preview Style

In example 6, ImageModifier is configured to customize the backplane style of the Image component.

```ts
// xxx.ets
import { ImageModifier } from '@kit.ArkUI';

@Entry
@Component
struct dragPreviewOptionsDemo{
  @State myModifier: ImageAttribute = new ImageModifier().opacity(0.5)
  @State vis: boolean = true
  @State changeValue: string = ''
  @State submitValue: string = ''
  @State positionInfo: CaretOffset = { index: 0, x: 0, y: 0 }
  controller: SearchController = new SearchController()
  @State OpacityIndex: number = 0
  @State OpacityList:(number | undefined | null)[]=[
    0.3,0.5,0.7,1,-50,0,10,undefined,null
  ]
  build() {
    Row() {
      Column() {
        Text(this.OpacityList[this.OpacityIndex] + "")
        Button("Opacity")
          .onClick(()=> {
            this.OpacityIndex++
            if(this.OpacityIndex > this.OpacityList.length - 1){
              this.OpacityIndex = 0
            }
          })
        Image($r('app.media.image'))
          .margin({ top: 10 })
          .width("100%")
          .draggable(true)
          .dragPreviewOptions({modifier: this.myModifier.opacity(this.OpacityList[this.OpacityIndex]) as ImageModifier})
      }
      .width("50%")
      .height("50%")
    }
  }
}
```

![imageModifier.gif](figures/imageModifier.gif)

### Example 7: Configuring Image Dragging Settings

Example 7 shows how to set components when different images (online image resources, local image resources, and PixelMap) are dragged.
The **ohos.permission.INTERNET** permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

```ts
// xxx.ets
import { uniformTypeDescriptor, unifiedDataChannel } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { request } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { buffer } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ImageDrag {
  @State targetImage1: string | PixelMap | null = null;
  @State targetImage2: string | PixelMap | null = null;
  @State targetImage3: string | PixelMap | null = null;
  context: Context | undefined = this.getUIContext().getHostContext();
  filesDir = this.context?.filesDir;

  public async createPixelMap(pixelMap: unifiedDataChannel.SystemDefinedPixelMap): Promise<image.PixelMap | null> {
    let mWidth: number = (pixelMap.details?.width ?? -1) as number;
    let mHeight: number = (pixelMap.details?.height ?? -1) as number;
    let mPixelFormat: image.PixelMapFormat =
      (pixelMap.details?.['pixel-format'] ?? image.PixelMapFormat.UNKNOWN) as image.PixelMapFormat;
    let mItemPixelMapData: Uint8Array = pixelMap.rawData;
    const opts: image.InitializationOptions = {
      editable: false, pixelFormat: mPixelFormat, size: {
        height: mHeight,
        width: mWidth
      }
    };
    const buffer: ArrayBuffer = mItemPixelMapData.buffer.slice(mItemPixelMapData.byteOffset,
      mItemPixelMapData.byteLength + mItemPixelMapData.byteOffset);
    try {
      let pixelMap: image.PixelMap = await image.createPixelMap(buffer, opts);
      return pixelMap;
    } catch (err) {
      console.error('dragtest--> getPixelMap', err);
      return null;
    }
  }

  build() {
    Column() {
      Flex({ direction: FlexDirection.Row, justifyContent: FlexAlign.Center }) {
        // Drag an online image.
        Column() {
          Text('Online Image').fontSize(14)
          Image('https://www.example.com/xxx.png')// Enter a specific network image address.
            .objectFit(ImageFit.Contain)
            .draggable(true)
            .onDragStart(() => {
            })
            .width(100)
            .height(100)
        }
        .border({
          width: 2,
          color: Color.Gray,
          radius: 5,
          style: BorderStyle.Dotted
        })
        .alignItems(HorizontalAlign.Center).justifyContent(FlexAlign.Center)

        // Drag a local image.
        Column() {
          Text('Local Image').fontSize(14)
          Image($r('app.media.example'))
            .objectFit(ImageFit.Contain)
            .draggable(true)
            .onDragStart(() => {
            })
            .width(100)
            .height(100)
        }
        .border({
          width: 2,
          color: Color.Gray,
          radius: 5,
          style: BorderStyle.Dotted
        })
        .alignItems(HorizontalAlign.Center).justifyContent(FlexAlign.Center)

        // Drag a PixelMap object.
        Column() {
          Text('PixelMap').fontSize(14)
          Image(this.context?.resourceManager.getDrawableDescriptor($r('app.media.example').id).getPixelMap())
            .objectFit(ImageFit.Contain)
            .draggable(true)
            .onDragStart(() => {
            })
            .width(100)
            .height(100)
        }
        .border({
          width: 2,
          color: Color.Gray,
          radius: 5,
          style: BorderStyle.Dotted
        })
        .alignItems(HorizontalAlign.Center).justifyContent(FlexAlign.Center)
      }

      // Set the drop data type to Image.
      Text('Data type is Image').fontSize(14).margin({ top: 10 })
      Column() {
        Image(this.targetImage1)
          .objectFit(ImageFit.Contain)
          .width('70%')
          .height('70%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((event: DragEvent, extraParams: string) => {
            if (extraParams === null || extraParams === undefined) {
              return;
            }
            // Obtain the image through extraParams.
            let arr: Record<string, object> = JSON.parse(extraParams) as Record<string, object>;
            let uri = arr['extraInfo'];
            if (typeof uri == 'string') {
              this.targetImage1 = uri;
              try {
                request.downloadFile(this.context, {
                  url: uri,
                  filePath: this.filesDir + '/example.png'
                }).then((downloadTask: request.DownloadTask) => {
                  let file = fileIo.openSync(this.filesDir + '/example.png', fileIo.OpenMode.READ_WRITE);
                  let arrayBuffer = new ArrayBuffer(1024);
                  let readLen = fileIo.readSync(file.fd, arrayBuffer);
                  let buf = buffer.from(arrayBuffer, 0, readLen);
                  console.info(`The content of file: ${buf.toString()}`);
                  fileIo.closeSync(file);
                })
              } catch (error) {
              }
            }
          })
      }
      .width('70%')
      .height('25%')
      .border({
        width: 2,
        color: Color.Gray,
        radius: 5,
        style: BorderStyle.Dotted
      })
      .alignItems(HorizontalAlign.Center)
      .justifyContent(FlexAlign.Center)

      Column() {
        Image(this.targetImage2)
          .objectFit(ImageFit.Contain)
          .width('70%')
          .height('70%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.IMAGE])
          .onDrop((event: DragEvent, extraParams: string) => {
            // Obtain the image through uniformTypeDescriptor.
            let data: UnifiedData = event.getData();
            let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
            if (records[0].getType() === uniformTypeDescriptor.UniformDataType.IMAGE) {
              let image: unifiedDataChannel.Image = records[0] as unifiedDataChannel.Image;
              this.targetImage2 = image.imageUri;
            }
          })
      }
      .width('70%')
      .height('25%')
      .border({
        width: 2,
        color: Color.Gray,
        radius: 5,
        style: BorderStyle.Dotted
      })
      .alignItems(HorizontalAlign.Center)
      .justifyContent(FlexAlign.Center)

      // Set the drop data type to PixelMap.
      Text('Data type is PixelMap').fontSize(14).margin({ top: 10 })
      Column() {
        Image(this.targetImage3)
          .objectFit(ImageFit.Contain)
          .width('70%')
          .height('70%')
          .allowDrop([uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP])
          .onDrop(async (event: DragEvent, extraParams: string) => {
            // Obtain the image through uniformTypeDescriptor.
            let data: UnifiedData = event.getData();
            let records: Array<unifiedDataChannel.UnifiedRecord> = data.getRecords();
            if (records[0].getType() === uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP) {
              let record: unifiedDataChannel.SystemDefinedPixelMap =
                records[0] as unifiedDataChannel.SystemDefinedPixelMap;
              this.targetImage3 = await this.createPixelMap(record);

              // Save data to local storage.
              const imagePackerApi = image.createImagePacker();
              let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 };
              const path: string = this.context?.cacheDir + "/pixel_map.jpg";
              let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
              imagePackerApi.packToFile(this.targetImage3, file.fd, packOpts).then(() => {
                // Pack the image into the file.
              }).catch((error: BusinessError) => {
                console.error('Failed to pack the image. And the error is: ' + error);
              })
            }
          })
      }
      .width('70%')
      .height('25%')
      .border({
        width: 2,
        color: Color.Gray,
        radius: 5,
        style: BorderStyle.Dotted
      })
      .alignItems(HorizontalAlign.Center)
      .justifyContent(FlexAlign.Center)

    }.width('100%').height('100%')
  }
}
```

![imageDrag.gif](figures/imageDrag.gif)

### Example 8: Enabling Haptic Feedback for Dragging
This example demonstrates how to enable haptic feedback for image dragging by setting **enableHapticFeedback**.
```ts
// xxx.ets
@Entry
@Component
struct DragPreviewDemo{
  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text("menu item 1")
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
      Divider()
        .height(5)
      Text("menu item 2")
        .fontSize(15)
        .width(100)
        .height(40)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Pink)
    }
    .width(100)
  }

  build() {
    Row() {
      Column() {
        Image($r('app.media.app_icon'))
          .width("30%")
          .draggable(true)
          .dragPreviewOptions({}, {isMultiSelectionEnabled:true, defaultAnimationBeforeLifting:true, enableHapticFeedback: true})
          .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
          .onDragStart(() => {
            console.info("Image onDragStart")
          })
      }
      .width("100%")
    }
    .height("100%")
  }
}
```

### Example 9: Customizing the Drag Preview
This example demonstrates how to customize the drag preview using **onlyForLifting** for lifting effects and **isLiftingDisabled** to disable the lifting effect.
```ts
// xxx.ets
@Entry
@Component
struct LiftingExampleDemo {
  @Builder
  dragPreviewBuilder() {
    Column() {
      Text("dragPreview builder")
        .width(150)
        .height(50)
        .fontSize(20)
        .borderRadius(10)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Green)
    }
  }
  @Builder
  MenuBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text("menu 1")
        .fontSize(25)
        .width(200)
        .height(60)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Green)
      Divider()
        .height(5)
      Text("menu 2")
        .fontSize(25)
        .width(200)
        .height(60)
        .textAlign(TextAlign.Center)
        .fontColor(Color.Black)
        .backgroundColor(Color.Green)
    }
    .width(100)
  }
  build() {
    Column() {
      Column() {
        Text("Lifting effect disabled")
          .fontSize(30)
          .height(30)
          .backgroundColor('#FFFFFF')
          .margin({ top: 30 })
        Image($r('app.media.startIcon'))
          .width("40%")
          .draggable(true)
          .margin({ top: 15 })
          .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
          .onDragStart(() => {
          })
          .dragPreviewOptions({}, {
            isLiftingDisabled: true
          })
          .dragPreview(this.dragPreviewBuilder, {
            onlyForLifting: true,
            delayCreating: true
          })
      }.width("%")
      Column() {
        Text("Lifting effect only")
          .fontSize(30)
          .height(30)
          .backgroundColor('#FFFFFF')
          .margin({ top: 80 })
        Image($r('app.media.startIcon'))
          .width("40%")
          .draggable(true)
          .margin({ top: 15 })
          .onDragStart(() => {
          })
          .dragPreviewOptions({}, {
            isLiftingDisabled: false
          })
          .dragPreview(this.dragPreviewBuilder, {
            onlyForLifting: true,
            delayCreating: true
          })
      }.width("100%")
    }.height("100%")
  }
}
```

Custom preview for the lifting effect only

![onlyForLifting.gif](figures/onlyForLifting.gif)

Custom preview with the lifting effect disabled

![isLiftingDisabled.gif](figures/isLiftingDisabled.gif)

### Example 10: Calculating the Follow-Point Position Based on the Initial Drag Preview Size
This example demonstrates how to calculate the follow-point position during dragging based on the initial drag preview size by configuring **DragPreviewMode.ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW**. When DragPreviewMode.ENABLE_MULTI_TILE_EFFECT is set, this attribute does not take effect.
```ts
@Entry
@Component
struct Index {
  private iconStr: ResourceStr = $r("app.media.app_icon")

  @Builder
  MyPreview() {
    Image($r('app.media.image'))
      .width(100)
      .height(100)
  }

  @Builder
  MyMenuPreview() {
    Column() {
      Image($r('app.media.image'))
        .width(100)
        .height(100)
    }
    .backgroundColor(Color.Green)
    .width(300)
    .height(300)
  }

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
    }
  }

  @Builder
  SubMenu() {
    Menu() {
      MenuItem({ content: "Copy", labelInfo: "Ctrl+C" })
      MenuItem({ content: "Paste", labelInfo: "Ctrl+V" })
    }
  }

  build() {
    NavDestination() {
      Scroll() {
        Column() {
          Text("no ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW")
          Image($r('app.media.image'))
            .width(200)
            .height(200)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress, {
              preview: this.MyPreview
            })
            .dragPreview(this.MyMenuPreview)
            .draggable(true)

          Text("ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW")
          Image($r('app.media.image'))
            .width(200)
            .height(200)
            .bindContextMenu(this.MyMenu, ResponseType.LongPress, {
              preview: this.MyPreview
            })
            .dragPreview(this.MyMenuPreview)
            .draggable(true)
            .dragPreviewOptions({
              mode: [DragPreviewMode.ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW]
            })
        }.width('100%')
      }
    }
    .height('100%')
    .width('100%')
  }
}
```



### Example 11: Implementing Transition Animation Between Long-press Preview and Drag Preview
Example 11 demonstrates different drag transition effects by configuring DraggingSizeChangeEffect.
```ts
@Entry
@Component
struct Index {
  private iconStr: ResourceStr = $r("app.media.app_icon")

  @Builder
  MyPreview() {
    Image($r('app.media.image'))
      .width(200)
      .height(200)
  }

  @Builder
  MyMenuPreviewSame() {
    Column() {
      Image($r('app.media.image'))
        .width(300)
        .height(300)
    }
  }

  @Builder
  MyMenuPreview() {
    Column() {
      Image($r('app.media.startIcon'))
        .width(300)
        .height(300)
    }
  }

  @Builder
  MyMenu() {
    Menu() {
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
      MenuItem({ startIcon: this.iconStr, content: "Menu option" })
    }
  }

  @Builder
  SubMenu() {
    Menu() {
      MenuItem({ content: "Copy", labelInfo: "Ctrl+C" })
      MenuItem({ content: "Paste", labelInfo: "Ctrl+V" })
    }
  }

  build() {
    Column() {
      Text("sizeChangeEffect: SIZE_TRANSITION - Long press to open menu, drag to transition from menu preview to drag preview with scaling effect (no overlay)"")
        .margin({ top: 10 })
      Image($r('app.media.image'))
        .width(200)
        .height(200)
        .bindContextMenu(this.MyMenu, ResponseType.LongPress, {
          preview: this.MyMenuPreviewSame
        })
        .dragPreview(this.MyPreview)
        .dragPreviewOptions({
          sizeChangeEffect: DraggingSizeChangeEffect.SIZE_TRANSITION
        })
        .draggable(true)

      Text("sizeChangeEffect: SIZE_CONTENT_TRANSITION - Long press to open menu, drag to transition with two-layer overlay effect (menu preview and drag preview)")
        .margin({ top: 10 })
      Image($r('app.media.image'))
        .width(200)
        .height(200)
        .bindContextMenu(this.MyMenu, ResponseType.LongPress, {
          preview: this.MyMenuPreview
        })
        .dragPreview(this.MyPreview)
        .dragPreviewOptions({
          sizeChangeEffect: DraggingSizeChangeEffect.SIZE_CONTENT_TRANSITION
        })
        .draggable(true)
    }
    .height('100%')
    .width('100%')
  }
}
```


