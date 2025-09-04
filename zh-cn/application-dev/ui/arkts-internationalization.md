# UI国际化
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

本文介绍如何实现应用程序UI界面的国际化，包含资源配置和镜像布局，关于应用适配国际化的详细参考，请参考[Localization Kit（本地化开发服务）](../internationalization/i18n-l10n.md)。

## 利用资源限定词配置国际化资源

在开发阶段，通过DevEco Studio，可以为应用在对应语言和地区的资源限定词目录下配置不同的资源，来实现UI国际化。详细介绍请参考[资源分类与访问](../quick-start/resource-categories-and-access.md)。

## 使用镜像能力

不同国家对文本对齐方式和读取顺序有所不同，例如英语采用从左到右的顺序，阿拉伯语和希腊语则采用从右到左（RTL）的顺序。为满足不同用户的阅读习惯，ArkUI提供了镜像能力。在特定情况下将显示内容在X轴上进行镜像反转，由从左向右显示变成从右向左显示。

| 镜像前          | 镜像后                                  |
| ----------- | ----------------------------------- |
|![](figures/mirroring_1-0.PNG)|![](figures/mirroring_1-1.PNG)|

当组件满足以下任意条件时，镜像能力生效：

1. 组件的direction属性设置为Direction.Rtl。

2. 组件的direction属性设置为Direction.Auto，且当前的系统语言（如维吾尔语）的阅读习惯是从右向左。

### 基本概念

- LTR：顺序为从左向右。
- RTL：顺序为从右向左。

### 使用约束

ArkUI 如下能力已默认适配镜像：

| 类别     | 名称                                                         |
| -------- | ------------------------------------------------------------ |
| 基础组件 | [Swiper](../reference/apis-arkui/arkui-ts/ts-container-swiper.md)、[Tabs](../reference/apis-arkui/arkui-ts/ts-container-tabs.md)、[TabContent](../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md)、[List](../reference/apis-arkui/arkui-ts/ts-container-list.md)、[Progress](../reference/apis-arkui/arkui-ts/ts-basic-components-progress.md)、[CalendarPicker](../reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)、[CalendarPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-calendarpicker-dialog.md)、[TextPicker](../reference/apis-arkui/arkui-ts/ts-basic-components-textpicker.md)、[TextPickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-textpicker-dialog.md)、[DatePicker](../reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md)、[DatePickerDialog](../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md)、[Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md)、[WaterFlow](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md)、[Scroll](../reference/apis-arkui/arkui-ts/ts-container-scroll.md)、[ScrollBar](../reference/apis-arkui/arkui-ts/ts-basic-components-scrollbar.md)、[AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md)、[Stepper](../reference/apis-arkui/arkui-ts/ts-basic-components-stepper.md)、[SideBarContainer](../reference/apis-arkui/arkui-ts/ts-container-sidebarcontainer.md)、[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)、[NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md)、[Rating](../reference/apis-arkui/arkui-ts/ts-basic-components-rating.md)、[Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md)、[Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md)、[Badge](../reference/apis-arkui/arkui-ts/ts-container-badge.md)、[Counter](../reference/apis-arkui/arkui-ts/ts-container-counter.md)、[Chip](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Chip.md)、[SegmentButton](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md)、[bindMenu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu)、[bindContextMenu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindcontextmenu8)、[TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)、[TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)、[Search](../reference/apis-arkui/arkui-ts/ts-basic-components-search.md)、[Stack](../reference/apis-arkui/arkui-ts/ts-container-stack.md)、[GridRow](../reference/apis-arkui/arkui-ts/ts-container-gridrow.md)、[Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)、[Select](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md)、[Marquee](../reference/apis-arkui/arkui-ts/ts-basic-components-marquee.md)、[Row](../reference/apis-arkui/arkui-ts/ts-container-row.md)、[Column](../reference/apis-arkui/arkui-ts/ts-container-column.md)、[Flex](../reference/apis-arkui/arkui-ts/ts-container-flex.md)、[RelativeContainer](../reference/apis-arkui/arkui-ts/ts-container-relativecontainer.md)、[ListItemGroup](../reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md) |
| 高级组件 | [SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md) 、[TreeView](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-TreeView.md) 、[Filter](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Filter.md)、[SplitLayout](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SplitLayout.md)、[ToolBar](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ToolBar.md)、[ComposeListItem](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ComposeListItem.md)、[EditableTitleBar](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-EditableTitleBar.md)、[ProgressButton](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ProgressButton.md)、[SubHeader](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SubHeader.md) 、[Popup](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Popup.md)、[Dialog](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Dialog.md)、[SwipeRefresher](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SwipeRefresher.md) |
| 通用属性 | [position](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#position)、[markAnchor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#markanchor)、[offset](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#offset)、[alignRules](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#alignrules12)、[borderWidth](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderwidth)、[borderColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#bordercolor)、[borderRadius](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderradius)、[padding](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#padding)、[margin](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin) |
| 接口     | [AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md)、[ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md)、[promptAction.showDialog](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowdialogdeprecated)、[promptAction.showToast](../reference/apis-arkui/js-apis-promptAction.md#promptactionshowtoastdeprecated) |

但如下三种场景还需要进行适配：

1. 界面布局、边框设置：关于方向类的通用属性，如果需要支持镜像能力，使用泛化的方向指示词 start/end入参类型替换 left/right、x/y等绝对方向指示词的入参类型，来表示自适应镜像能力。

2. Canvas组件只有限支持文本绘制的镜像能力。

3. XComponent组件不支持组件镜像能力。

### 界面布局和边框设置

目前，以下三类通用属性需要使用新入参类型适配：

位置设置：[position](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#position)、[markAnchor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#markanchor)、[offset](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#offset)、[alignRules](../reference/apis-arkui/arkui-ts/ts-universal-attributes-location.md#alignrules12)

边框设置：[borderWidth](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderwidth)、[borderColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#bordercolor)、[borderRadius](../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderradius)

尺寸设置：[padding](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#padding)、[margin](../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)

以position为例，需要把绝对方向x、y描述改为新入参类型start、end的描述，其他属性类似。

```typeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index1 {
  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Stack({ alignContent: Alignment.TopStart }) {
        Column()
          .width(100)
          .height(100)
          .backgroundColor(Color.Red)
          .position({ start: LengthMetrics.px(200), top: LengthMetrics.px(200) })  //需要同时支持LTR和RTL时使用API12新增的LocalizedEdges入参类型,
                                                                                   //仅支持LTR时等同于.position({ x: '200px', y: '200px' })

      }.backgroundColor(Color.Blue)
    }.width("100%").height("100%").border({ color: '#880606' })
  }
}
```

### 自定义绘制Canvas组件

Canvas组件的绘制内容和坐标均不支持镜像能力。已绘制到Canvas组件上的内容并不会跟随系统语言的切换自动做镜像效果。

[CanvasRenderingContext2D](../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)的文本绘制支持镜像能力，在使用时需要与Canvas组件的通用属性direction（组件显示方向）和CanvasRenderingContext2D的属性direction（文本绘制方向）协同使用。具体规格如下：

1. 优先级：CanvasRenderingContext2D的direction属性 > Canvas组件通用属性direction > 系统语言决定的水平显示方向。
2. Canvas组件本身不会自动跟随系统语言切换镜像效果，需要应用监听到系统语言切换后自行重新绘制。
3. CanvasRenderingContext2D绘制文本时，只有符号等文本会对绘制方向生效，英文字母和数字不响应绘制方向的变化。

```typeScript
import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello world';
  private settings: RenderingContextSettings = new RenderingContextSettings(true)
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings)

  aboutToAppear(): void {
    // 监听系统语言切换
    let subscriber: commonEventManager.CommonEventSubscriber | null = null;
    let subscribeInfo2: commonEventManager.CommonEventSubscribeInfo = {
      events: ["usual.event.LOCALE_CHANGED"],
    }
    commonEventManager.createSubscriber(subscribeInfo2, (err: BusinessError, data: commonEventManager.CommonEventSubscriber) => {
      if (err) {
        console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
        return;
      }

      subscriber = data;
      if (subscriber !== null) {
        commonEventManager.subscribe(subscriber, (err: BusinessError, data: commonEventManager.CommonEventData) => {
          if (err) {
            console.error(`订阅语言地区状态变化公共事件失败. Code is ${err.code}, message is ${err.message}`);
            return;
          }
          console.info('成功订阅语言地区状态变化公共事件: data: ' + JSON.stringify(data))
          // 监听到语言切换后，需要重新绘制Canvas内容
          this.drawText();
        })
      } else {
        console.error(`MayTest Need create subscriber`);
      }
    })
  }

  drawText(): void {
    console.error("MayTest drawText")
    this.context.reset()
    this.context.direction = "inherit"
    this.context.font = '30px sans-serif'
    this.context.fillText("ab%123&*@", 50, 50)
  }

  build() {
    Row() {
      Canvas(this.context)
        .direction(Direction.Auto)
        .width("100%")
        .height("100%")
        .onReady(() =>{
          this.drawText()
        })
        .backgroundColor(Color.Pink)
    }
    .height('100%')
  }

}
```

| 镜像前          | 镜像后                                  |
| ----------- | ----------------------------------- |
|![](figures/mirroring_2-0.jpg)|![](figures/mirroring_2-1.jpg)|

### 镜像状态字符对齐
[Direction](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#direction)是指文字的方向，即文本在屏幕上呈现时字符的顺序。在从左到右（LTR）文本中，显示顺序是从左向右；在从右到左（RTL）文本中，显示顺序是从右向左。

[TextAlign](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#textalign)是将文本作为一个整体，在布局上的影响，具体位置会受Direction影响，以TextAlign为start为例，当Direction为LTR时，布局位置靠左；当Direction为RTL时，布局位置靠右。

在LTR与RTL文本混排时，如一个英文句子中包含阿拉伯语的单词或短语，显示顺序将变得复杂。下图为数字和维吾尔语混合时对应的字符逻辑顺序。

![alt text](figures/image-8.png)

此时，文本渲染引擎会采用名为“双向算法”或“Unicode双向算法”（Unicode Bidirectional Algorithm）的方法来确定字符的显示顺序。下图展示了LTR与RTL文本混合时对应的字符显示顺序，确定字符方向的基本原则如下：
1. 强字符的方向性：强字符具有明确的方向性，例如，中文为LTR，阿拉伯语为RTL，这类字符的方向性会影响其周围的中性字符。

2. 弱字符的方向性：弱字符不具备明确的方向性，这些字符不会影响其周围中性字符的方向。

3. 中性字符的方向性：中性字符无固定方向性，它们会继承其最近的强字符的方向；若附近无强字符，则采用全局方向。

![alt text](figures/image-1.png)