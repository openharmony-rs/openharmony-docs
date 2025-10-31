# 共享元素转场 (一镜到底)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @ge-yafang-->

共享元素转场是一种界面切换时对相同或者相似的两个元素做的一种位置和大小匹配的过渡动画效果，也称一镜到底动效。

如下例所示，在点击图片后，该图片消失，同时在另一个位置出现新的图片，二者之间内容相同，可以对它们添加一镜到底动效。左图为不添加一镜到底动效的效果，右图为添加一镜到底动效的效果，一镜到底的效果能够让二者的出现消失产生联动，使得内容切换过程显得灵动自然而不生硬。

![zh-cn_image_0000001599644876](figures/zh-cn_image_0000001599644876.gif)|![zh-cn_image_0000001599644877](figures/zh-cn_image_0000001599644877.gif)
---|---

一镜到底的动效有多种实现方式，在实际开发过程中，应根据具体场景选择合适的方法进行实现。

以下是不同实现方式的对比：

| 一镜到底实现方式 | 特点 | 适用场景 |
| ------ | ---- | ---- |
| 不新建容器直接变化原容器 | 不发生路由跳转，需要在一个组件中实现展开及关闭两种状态的布局，展开后组件层级不变。| 适用于转场开销小的简单场景，如点开页面无需加载大量数据及组件。 |
| 新建容器并跨容器迁移组件 | 通过使用NodeController，将组件从一个容器迁移到另一个容器，在开始迁移时，需要根据前后两个布局的位置大小等信息对组件添加位移及缩放，确保迁移开始时组件能够对齐初始布局，避免出现视觉上的跳变现象。之后再添加动画将位移及缩放等属性复位，实现组件从初始布局到目标布局的一镜到底过渡效果。 | 适用于新建对象开销大的场景，如视频直播组件点击转为全屏等。 |
| 使用geometryTransition共享元素转场 | 利用系统能力，转场前后两个组件调用geometryTransition接口绑定同一id，同时将转场逻辑置于animateTo动画闭包内，这样系统侧会自动为二者添加一镜到底的过渡效果。 | 系统将调整绑定的两个组件的宽高及位置至相同值，并切换二者的透明度，以实现一镜到底过渡效果。因此，为了实现流畅的动画效果，需要确保对绑定geometryTransition的节点添加宽高动画不会有跳变。此方式适用于创建新节点开销小的场景。 |

## 不新建容器并直接变化原容器

该方法不新建容器，通过在已有容器上增删组件触发[transition](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md)，搭配组件[属性动画](./arkts-attribute-animation-apis.md)实现一镜到底效果。

对于同一个容器展开，容器内兄弟组件消失或者出现的场景，可通过对同一个容器展开前后进行宽高位置变化并配置属性动画，对兄弟组件配置出现消失转场动画实现一镜到底效果。基本步骤为：

1. 构建需要展开的页面，并通过状态变量构建好普通状态和展开状态的界面。

2. 将需要展开的页面展开，通过状态变量控制兄弟组件消失或出现，并通过绑定出现消失转场实现兄弟组件转场效果。

以点击卡片后显示卡片内容详情场景为例：

<!-- @[post_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template2/Index.ets) -->

![zh-cn_image_0000001600653160](figures/zh-cn_image_0000001600653160.gif)

## 新建容器并跨容器迁移组件

通过[NodeContainer](../reference/apis-arkui/arkui-ts/ts-basic-components-nodecontainer.md)[自定义占位节点](arkts-user-defined-place-holder.md)，利用[NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md)实现组件的跨节点迁移，配合属性动画给组件的迁移过程赋予一镜到底效果。这种一镜到底的实现方式可以结合多种转场方式使用，如导航转场（[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)）、半模态转场（[bindSheet](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)）等。

### 结合Stack使用

可以利用Stack内后定义组件在最上方的特性控制组件在跨节点迁移后位z序最高，以展开收起卡片的场景为例，实现步骤为：

- 展开卡片时，获取节点A的位置信息，将其中的组件迁移到与节点A位置一致的节点B处，节点B的层级高于节点A。

- 对节点B添加属性动画，使之展开并运动到展开后的位置，完成一镜到底的动画效果。

- 收起卡片时，对节点B添加属性动画，使之收起并运动到收起时的位置，即节点A的位置，实现一镜到底的动画效果。

- 在动画结束时利用回调将节点B中的组件迁移回节点A处。

<!-- @[stack_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template3/Index.ets) -->

<!-- @[stack_post_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template3/PostNode.ets) -->

![zh_cn_image_sharedElementsNodeTransfer](figures/zh-cn_image_sharedElementsNodeTransfer.gif)

### 结合Navigation使用

可以利用[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)的自定义导航转场动画能力（[customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11)，可参考Navigation[示例3](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例3设置可交互转场动画)）实现一镜到底动效。共享元素转场期间，组件由消失页面迁移至出现页面。

以展开收起缩略图的场景为例，实现步骤为：

- 通过customNavContentTransition配置PageOne与PageTwo的自定义导航转场动画。

- 自定义的共享元素转场效果由属性动画实现，具体实现方式为抓取页面内组件相对窗口的位置信息从而正确匹配组件在PageOne与PageTwo的位置、缩放等，即动画开始和结束的属性信息。

- 点击缩略图后共享元素组件从PageOne被迁移至PageTwo，随后触发由PageOne至PageTwo的自定义转场动画，即PageTwo的共享元素组件从原来的缩略图状态做动画到全屏状态。

- 由全屏状态返回到缩略图时，触发由PageTwo至PageOne的自定义转场动画，即PageTwo的共享元素组件从全屏状态做动画到原PageOne的缩略图状态，转场结束后共享元素组件从PageTwo被迁移回PageOne。

```
├──entry/src/main/ets                 // 代码区
│  ├──CustomTransition
│  │  ├──AnimationProperties.ets      // 一镜到底转场动画封装
│  │  └──CustomNavigationUtils.ets    // Navigation自定义转场动画配置
│  ├──entryability
│  │  └──EntryAbility.ets             // 程序入口类
│  ├──NodeContainer
│  │  └──CustomComponent.ets          // 自定义占位节点
│  ├──pages
│  │  ├──Index.ets                    // 导航页面
│  │  ├──PageOne.ets                  // 缩略图页面
│  │  └──PageTwo.ets                  // 全屏展开页面
│  └──utils
│     ├──ComponentAttrUtils.ets       // 组件位置获取
│     └──WindowUtils.ets              // 窗口信息
└──entry/src/main/resources           // 资源文件
```

<!-- @[navigation_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template4/Index.ets) -->

<!-- @[navigation_page_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template4/PageOne.ets) -->

<!-- @[navigation_page_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template4/PageTwo.ets) -->

<!-- @[custom_navigation_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/CustomTransition/CustomNavigationUtils.ets) -->

<!-- -->
```ts
// 工程配置文件module.json5中配置 {"routerMap": "$profile:route_map"}
// route_map.json
{
  "routerMap": [
    {
      "name": "PageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder"
    },
    {
      "name": "PageTwo",
      "pageSourceFile": "src/main/ets/pages/PageTwo.ets",
      "buildFunction": "PageTwoBuilder"
    }
  ]
}
```

<!-- @[navigation_animation_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/CustomTransition/AnimationProperties.ets) -->

<!-- @[bind_sheet_component_attr_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/utils/ComponentAttrUtils.ets) -->

<!-- @[bind_sheet_window_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/utils/WindowUtils.ets) -->

<!-- @[bind_sheet_entry_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/entryability/EntryAbility.ets) -->

<!-- @[navigation_custom_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/NodeContainer/CustomComponent.ets) -->

![zh-cn_image_NavigationNodeTransfer](figures/zh-cn_image_NavigationNodeTransfer.gif)

### 结合BindSheet使用

想实现半模态转场（[bindSheet](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)）的同时，组件从初始界面做一镜到底动画到半模态页面的效果，可以使用这样的设计思路。将[SheetOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#sheetoptions)中的mode设置为SheetMode.EMBEDDED，该模式下新起的页面可以覆盖在半模态弹窗上，页面返回后该半模态依旧存在，半模态面板内容不丢失。在半模态转场的同时设置一全模态转场（[bindContentCover](../reference/apis-arkui/arkui-ts/ts-universal-attributes-modal-transition.md#bindcontentcover)）页面无转场出现，该页面仅有需要做共享元素转场的组件，通过属性动画，展示组件从初始界面至半模态页面的一镜到底动效，并在动画结束时关闭页面，并将该组件迁移至半模态页面。

以点击图片展开半模态页的场景为例，实现步骤为：

- 在初始界面挂载半模态转场和全模态转场两个页面，半模态页按需布局，全模态页面仅放置一镜到底动效需要的组件，抓取布局信息，使其初始位置为初始界面图片的位置。点击初始界面图片时，同时触发半模态和全模态页面出现，因设置为SheetMode.EMBEDDED模式，此时全模态页面层级最高。

- 设置不可见的占位图片置于半模态页上，作为一镜到底动效结束时图片的终止位置。利用[布局回调](../reference/apis-arkui/js-apis-arkui-inspector.md)监听该占位图片布局完成的时候，此时执行回调抓取占位图片的位置信息，随后全模态页面上的图片利用属性动画开始进行共享元素转场。

- 全模态页面的动画结束时触发结束回调，关闭全模态页面，将共享元素图片的节点迁移至半模态页面，替换占位图片。

- 需注意，半模态页面的弹起高度不同，其页面起始位置也有所不同，而全模态则是全屏显示，两者存在一高度差，做一镜到底动画时，需要计算差值并进行修正，具体可见demo。

- 还可以配合一镜到底动画，给初始界面图片也增加一个从透明到出现的动画，使得动效更为流畅。

```
├──entry/src/main/ets                 // 代码区
│  ├──entryability
│  │  └──EntryAbility.ets             // 程序入口类
│  ├──NodeContainer
│  │  └──CustomComponent.ets          // 自定义占位节点
│  ├──pages
│  │  └──Index.ets                    // 进行共享元素转场的主页面
│  └──utils
│     ├──ComponentAttrUtils.ets       // 组件位置获取
│     └──WindowUtils.ets              // 窗口信息
└──entry/src/main/resources           // 资源文件
```

```ts
// index.ets
import { MyNodeController, createMyNode, getMyNode } from '../NodeContainer/CustomComponent';
import { ComponentAttrUtils, RectInfoInPx } from '../utils/ComponentAttrUtils';
import { WindowUtils } from '../utils/WindowUtils';
import { inspector } from '@kit.ArkUI'

class AnimationInfo {
  scale: number = 0;
  translateX: number = 0;
  translateY: number = 0;
  clipWidth: Dimension = 0;
  clipHeight: Dimension = 0;
}

@Entry
@Component
struct Index {
  @State isShowSheet: boolean = false;
  @State isShowImage: boolean = false;
  @State isShowOverlay: boolean = false;
  @State isAnimating: boolean = false;
  @State isEnabled: boolean = true;

  @State scaleValue: number = 0;
  @State translateX: number = 0;
  @State translateY: number = 0;
  @State clipWidth: Dimension = 0;
  @State clipHeight: Dimension = 0;
  @State radius: number = 0;
  // 原图的透明度
  @State opacityDegree: number = 1;

  // 抓取照片原位置信息
  private originInfo: AnimationInfo = new AnimationInfo;
  // 抓取照片在半模态页上位置信息
  private targetInfo: AnimationInfo = new AnimationInfo;
  // 半模态高度
  private bindSheetHeight: number = 450;
  // 半模态上图片圆角
  private sheetRadius: number = 20;

  // 设置半模态上图片的布局监听
  listener:inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('target');
  aboutToAppear(): void {
    // 设置半模态上图片的布局完成回调
    let onLayoutComplete:()=>void=():void=>{
      // 目标图片布局完成时抓取布局信息
      this.targetInfo = this.calculateData('target');
      // 仅半模态正确布局且此时无动画时触发一镜到底动画
      if (this.targetInfo.scale != 0 && this.targetInfo.clipWidth != 0 && this.targetInfo.clipHeight != 0 && !this.isAnimating) {
        this.isAnimating = true;
        // 用于一镜到底的模态页的属性动画
        this.getUIContext()?.animateTo({
          duration: 1000,
          curve: Curve.Friction,
          onFinish: () => {
            // 模态转场页（overlay）上的自定义节点下树
            this.isShowOverlay = false;
            // 半模态上的自定义节点上树，由此完成节点迁移
            this.isShowImage = true;
          }
        }, () => {
          this.scaleValue = this.targetInfo.scale;
          this.translateX = this.targetInfo.translateX;
          this.clipWidth = this.targetInfo.clipWidth;
          this.clipHeight = this.targetInfo.clipHeight;
          // 修正因半模态高度和缩放导致的高度差
          this.translateY = this.targetInfo.translateY +
            (this.getUIContext().px2vp(WindowUtils.windowHeight_px) - this.bindSheetHeight
              - this.getUIContext().px2vp(WindowUtils.navigationIndicatorHeight_px) - this.getUIContext().px2vp(WindowUtils.topAvoidAreaHeight_px));
          // 修正因缩放导致的圆角差异
          this.radius = this.sheetRadius / this.scaleValue
        })
        // 原图从透明到出现的动画
        this.getUIContext()?.animateTo({
          duration: 2000,
          curve: Curve.Friction,
        }, () => {
          this.opacityDegree = 1;
        })
      }
    }
    // 打开布局监听
    this.listener.on('layout', onLayoutComplete)
  }

  // 获取对应id的组件相对窗口左上角的属性
  calculateData(id: string): AnimationInfo {
    let itemInfo: RectInfoInPx =
      ComponentAttrUtils.getRectInfoById(WindowUtils.window.getUIContext(), id);
    // 首先计算图片的宽高与窗口宽高的比例
    let widthScaleRatio = itemInfo.width / WindowUtils.windowWidth_px;
    let heightScaleRatio = itemInfo.height / WindowUtils.windowHeight_px;
    let isUseWidthScale = widthScaleRatio > heightScaleRatio;
    let itemScale: number = isUseWidthScale ? widthScaleRatio : heightScaleRatio;
    let itemTranslateX: number = 0;
    let itemClipWidth: Dimension = 0;
    let itemClipHeight: Dimension = 0;
    let itemTranslateY: number = 0;

    if (isUseWidthScale) {
      itemTranslateX = this.getUIContext().px2vp(itemInfo.left - (WindowUtils.windowWidth_px - itemInfo.width) / 2);
      itemClipWidth = '100%';
      itemClipHeight = this.getUIContext().px2vp((itemInfo.height) / itemScale);
      itemTranslateY = this.getUIContext().px2vp(itemInfo.top - ((this.getUIContext().vp2px(itemClipHeight) - this.getUIContext().vp2px(itemClipHeight) * itemScale) / 2));
    } else {
      itemTranslateY = this.getUIContext().px2vp(itemInfo.top - (WindowUtils.windowHeight_px - itemInfo.height) / 2);
      itemClipHeight = '100%';
      itemClipWidth = this.getUIContext().px2vp((itemInfo.width) / itemScale);
      itemTranslateX = this.getUIContext().px2vp(itemInfo.left - (WindowUtils.windowWidth_px / 2 - itemInfo.width / 2));
    }

    return {
      scale: itemScale,
      translateX: itemTranslateX ,
      translateY: itemTranslateY,
      clipWidth: itemClipWidth,
      clipHeight: itemClipHeight,
    }
  }

  // 照片页
  build() {
    Column() {
      Text('照片')
        .textAlign(TextAlign.Start)
        .width('100%')
        .fontSize(30)
        .padding(20)
      // 图片使用Resource资源，需用户自定义
      Image($r("app.media.flower"))
        .opacity(this.opacityDegree)
        .width('90%')
        .id('origin')// 挂载半模态页
        .enabled(this.isEnabled)
        .onClick(() => {
          // 获取原始图像的位置信息，将模态页上图片移动缩放至该位置
          this.originInfo = this.calculateData('origin');
          this.scaleValue = this.originInfo.scale;
          this.translateX = this.originInfo.translateX;
          this.translateY = this.originInfo.translateY;
          this.clipWidth = this.originInfo.clipWidth;
          this.clipHeight = this.originInfo.clipHeight;
          this.radius = 0;
          this.opacityDegree = 0;
          // 启动半模态页和模态页
          this.isShowSheet = true;
          this.isShowOverlay = true;
          // 设置原图为不可交互抗打断
          this.isEnabled = false;
        })
    }
    .width('100%')
    .height('100%')
    .padding({ top: 20 })
    .alignItems(HorizontalAlign.Center)
    .bindSheet(this.isShowSheet, this.mySheet(), {
      // Embedded模式使得其他页面可以高于半模态页
      mode: SheetMode.EMBEDDED,
      height: this.bindSheetHeight,
      onDisappear: () => {
        // 保证半模态消失时状态正确
        this.isShowImage = false;
        this.isShowSheet = false;
        // 设置一镜到底动画又进入可触发状态
        this.isAnimating = false;
        // 原图重新变为可交互状态
        this.isEnabled = true;
      }
    }) // 挂载模态页作为一镜到底动画的实现页
    .bindContentCover(this.isShowOverlay, this.overlayNode(), {
      // 模态页面设置为无转场
      transition: TransitionEffect.IDENTITY,
    })
  }

  // 半模态页面
  @Builder
  mySheet() {
    Column({space: 20}) {
      Text('半模态页面')
        .fontSize(30)
      Row({space: 40}) {
        Column({space: 20}) {
          ForEach([1, 2, 3, 4], () => {
            Stack()
              .backgroundColor(Color.Pink)
              .borderRadius(20)
              .width(60)
              .height(60)
          })
        }
        Column() {
          if (this.isShowImage) {
            // 半模态页面的自定义图片节点
            ImageNode()
          }
          else {
            // 抓取布局和占位用，实际不显示
            // 图片使用Resource资源，需用户自定义
            Image($r("app.media.flower"))
              .visibility(Visibility.Hidden)
          }
        }
        .height(300)
        .width(200)
        .borderRadius(20)
        .clip(true)
        .id('target')
      }
      .alignItems(VerticalAlign.Top)
    }
    .alignItems(HorizontalAlign.Start)
    .height('100%')
    .width('100%')
    .margin(40)
  }

  @Builder
  overlayNode() {
    // Stack需要设置alignContent为TopStart，否则在高度变化过程中，截图和内容都会随高度重新布局位置
    Stack({ alignContent: Alignment.TopStart }) {
      ImageNode()
    }
    .scale({ x: this.scaleValue, y: this.scaleValue, centerX: undefined, centerY: undefined})
    .translate({ x: this.translateX, y: this.translateY })
    .width(this.clipWidth)
    .height(this.clipHeight)
    .borderRadius(this.radius)
    .clip(true)
  }
}

@Component
struct ImageNode {
  @State myNodeController: MyNodeController | undefined = new MyNodeController(false);

  aboutToAppear(): void {
    // 获取自定义节点
    let node = getMyNode();
    if (node == undefined) {
      // 新建自定义节点
      createMyNode(this.getUIContext());
    }
    this.myNodeController = getMyNode();
  }

  aboutToDisappear(): void {
    if (this.myNodeController != undefined) {
      // 节点下树
      this.myNodeController.onRemove();
    }
  }
  build() {
    NodeContainer(this.myNodeController)
  }
}
```

<!-- @[bind_custom_component](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/NodeContainer/CustomComponentBindSheet.ets) -->

<!-- @[bind_sheet_component_attr_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/utils/ComponentAttrUtils.ets) -->

<!-- @[bind_sheet_window_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/utils/WindowUtils.ets) -->

<!-- @[bind_sheet_entry_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/entryability/EntryAbility.ets) -->

![zh-cn_image_BindSheetNodeTransfer](figures/zh-cn_image_BindSheetNodeTransfer.gif)

## 使用geometryTransition共享元素转场

[geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md)用于组件内隐式共享元素转场，在视图状态切换过程中提供丝滑的上下文继承过渡体验。

geometryTransition的使用方式为对需要添加一镜到底动效的两个组件使用geometryTransition接口绑定同一id，这样在其中一个组件消失同时另一个组件创建出现的时候，系统会对二者添加一镜到底动效。

geometryTransition绑定两个对象的实现方式使得geometryTransition区别于其他方法，最适合用于两个不同对象之间完成一镜到底。

### geometryTransition的简单使用

对于同一个页面中的两个元素的一镜到底效果，geometryTransition接口的简单使用示例如下：

<!-- @[geometry_transition_simple](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template6/IfElseGeometryTransition.ets) -->

![zh-cn_image_0000001599644878](figures/zh-cn_image_0000001599644878.gif)

### geometryTransition结合模态转场使用

更多的场景中，需要对一个页面的元素与另一个页面的元素添加一镜到底动效。可以通过geometryTransition搭配模态转场接口实现。以点击头像弹出个人信息页的demo为例：

<!-- @[geometry_transition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/shareTransition/template7/Index.ets) -->

效果为点击主页的头像后，弹出模态页面显示个人信息，并且两个页面之间的头像做一镜到底动效：

![zh-cn_image_0000001597320327](figures/zh-cn_image_0000001597320327.gif)

<!--RP1--><!--RP1End-->