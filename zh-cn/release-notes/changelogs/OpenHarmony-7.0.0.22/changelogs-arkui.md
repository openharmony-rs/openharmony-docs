# ArkUI子系统Changelog

## cl.arkui.1 WithTheme相关组件行为变更

**访问级别**

公开接口

**变更原因**

为提升主题功能的一致性与完整性，对下述场景下的组件行为进行优化适配。

1. 当前已支持[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)的组件，在特定场景下部分组件未能正确应用[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)所设置的主题样式，与预期设计效果不符。
   - 弹窗类组件不跟随宿主节点的局部主题或深浅色样式。
   - 部分组件（组件范围见**场景二**）动态添加至[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)中后，不会跟随局部主题或深浅色变化而变化（例如通过ForEach+ListItem，将组件添加到WithTheme组件下）。

2. 对于暂不支持[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)的组件，其样式不会响应WithTheme或默认主题[setDefaultTheme](../../../application-dev/reference/apis-arkui/js-apis-arkui-theme.md#setdefaulttheme)设置的主题样式。

**变更影响**

此变更涉及应用适配。

**场景一：弹窗类组件跟随宿主节点的WithTheme样式**

变更前：宿主节点的[bindMenu](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu11)、[bindPopup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#bindpopup)、[bindSheet](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)、[CalendarPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)弹窗类组件弹出时，不跟随宿主节点的局部主题或深浅色样式。

变更后：宿主节点的[bindMenu](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu11)、[bindPopup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#bindpopup)、[bindSheet](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)、[CalendarPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)弹窗类组件弹出时，会跟随宿主节点的局部主题或深浅色样式。


**场景二：动态添加到WithTheme的组件响应主题变化**

变更前：当WithTheme的主题样式或深浅色发生动态变化时，后续动态添加到WithTheme中的组件不会同步响应这些变化。

变更后：当WithTheme的主题样式或深浅色发生动态变化时，后续动态添加到WithTheme中的组件会同步响应这些变化。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 动态添加场景 | [Button](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-button.md)、[Menu](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-menu.md)、[DatePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md)、[TextPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textpicker.md)、[TimePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-timepicker.md)、[Counter](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-counter.md)、[Progress](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-progress.md)、[TextClock](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textclock.md)、[LoadingProgress](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-loadingprogress.md)、[Scroll](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-scroll.md)、[AlphabetIndexer](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md)、[Tabs](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabs.md)、[TabContent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabcontent.md)、[Swiper](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-swiper.md)、[Indicator](../../../application-dev/reference/apis-arkui/arkui-ts/ts-swiper-components-indicator.md)。 |

**场景三：组件新增WithTheme支持能力**

变更前：组件不受WithTheme或setDefaultTheme设置的样式影响，显示为系统默认样式。

变更后：组件会响应WithTheme或setDefaultTheme设置的样式，并优先显示对应的主题效果。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 组件新增WithTheme支持能力 | [TextArea](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)、[Search](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-search.md)、[RichEditor](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md)、[Image](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-image.md)、[ImageAnimator](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-imageanimator.md)、[PatternLock](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-patternlock.md)、[QRCode](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-qrcode.md)、[DataPanel](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-datapanel.md)、[文本选择菜单](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-text.md)、[Badge](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-badge.md)、[styleString](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md)、[LocalBuilder](../../../application-dev/ui/state-management/arkts-localBuilder.md)、[Tabs](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabs.md)、[TabContent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabcontent.md)、[ListItemGroup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md)、[ListItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-listitem.md)、[ArcListItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-arclistitem.md)、[GridItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-griditem.md)、[Refresh](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-refresh.md)、[TextPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textpicker.md)、[TimePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-timepicker.md)、[DatePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md)、[CalendarPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)、[UIPickerComponent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md)、[MenuItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-menuitem.md)和[menuItemGroup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-menuitemgroup.md)。 |

**起始API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

WithThemeInterface、setDefaultTheme。

**适配指导**

1. 若希望上述组件在WithTheme下保持变更前的行为，即继续跟随系统样式或系统深浅色模式，可将该组件放入`WithTheme({ colorMode: ThemeColorMode.SYSTEM })`组件下。

   ```ts
   @Entry
   @Component
   struct WithThemeExample {
     @State message: string = 'Hello World';
     @State arr: number[] = [];
     private index: number = 0;
     build() {
       Row() {
         Column() {
           Button("Add Element")
             .onClick(() => {
               this.arr.push(this.index++);
             })
           WithTheme({ colorMode: ThemeColorMode.DARK }) {
             List() {
               ForEach(this.arr, (item: number, index) => {
                 ListItem() {
                   Column() {
                     WithTheme({ colorMode: ThemeColorMode.SYSTEM }) {
                       Column() {
                         Button("Button In ForEach with COLOR_MODE_SYSTEM")
                       }
                     }
                   }
                 }
               })
             }
             .width('100%')
             .height('100%')
           }
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

2. 如果WithTheme容器内的部分组件使用了固定颜色值，组件放入WithTheme中，生效WithTheme设置的样式时，可能影响显示效果。可通过将该组件放入新的WithTheme容器中，并将该容器的colorMode设置为ThemeColorMode.SYSTEM，恢复为变更前的行为。

   ```ts
   @Entry
   @Component
   struct WithThemeExample {
     @State arr: number[] = [];
     private index: number = 0
   
     build() {
       Row() {
         Column() {
           Button("Add Element")
             .onClick(() => {
               this.arr.push(this.index++);
             })
           WithTheme({ colorMode: ThemeColorMode.DARK }) {
             List() {
               ForEach(this.arr, (item: number, index) => {
                 ListItem() {
                   WithTheme({ colorMode: ThemeColorMode.SYSTEM }) {
                     Column() {
                       Text("Set ColorMode SYSTEM")
                         .fontColor("#FF383838")
                     }
                     .backgroundColor($r('sys.color.background_primary'))
   
                   }
                 }
               })
             }
             .width('100%')
             .height('100%')
           }
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

## cl.arkui.2 ArkUI接口新增仅支持Stage模型的约束

**访问级别**

公共能力

**变更原因**

ArkUI存在API接口未明确标注所支持的模型标签，导致DevEco Studio和开发者无法准确感知FA模型和Stage模型的支持情况。

**变更影响**

此变更涉及应用适配。

变更前：ArkUI提供的API version 10及以上版本的接口，如果未明确标注模型标签，可在FA模型工程中使用。

变更后：ArkUI提供的API version 10及以上版本的接口，均补充仅支持Stage模型的标签，此时接口无法在FA模型中使用，会产生编译报错。

**起始 API Level**

10

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

ArkUI API version 10及以上的全量接口。

**适配指导**

推荐使用Stage模型。Stage模型是当前系统主推的应用模型，请参考[Stage模型开发概述](../../../application-dev/application-models/stage-model-development-overview.md)和[FA模型开发概述](../../../application-dev/application-models/fa-model-development-overview.md)了解模型差异，进行应用适配。 

## cl.arkui.3 主页NavDestination中使用queryNavDestinationInfo接口的行为变更

**访问级别**

公共能力

**变更原因**

通过queryNavDestinationInfo(isInner: Optional&lt;boolean&gt;)接口无法获取到主页NavDestination的信息，不符合接口设计规格。

**变更影响**

变更前：通过入参包含HomePathInfo的Navigation接口，指定一个NavDestination作为Navigation主页后，通过[queryNavDestinationInfo](../../../application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-api.md#querynavdestinationinfo18)接口无法获取主页NavDestination的信息。

变更后：通过[queryNavDestinationInfo](../../../application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-api.md#querynavdestinationinfo18)接口能够获取主页NavDestination的信息。

**起始 API Level**

20

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

[queryNavDestinationInfo(isInner: Optional&lt;boolean&gt;)](../../../application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-api.md#querynavdestinationinfo18)接口。

**适配指导**

开发者需要根据变更内容审视自身业务代码是否需要进行适配，下面的示例代码展示了主页NavDestination中使用queryNavDestinationInfo接口在变更前后的差异。

```ts
import hilog from '@ohos.hilog';

@Component
struct MyPage {
  build() {
    NavDestination() {
    }
    .width('100%')
    .height('100%')
    .title('DetailPage')
  }
}

@Component
struct InnerCustomComponent {
  GetDestInfo() {
    // 向上查找当前自定义组件的所在的NavDestination
    let info = this.queryNavDestinationInfo(false);
    if (info) {
      // 变更后能够获取到主页NavDestination的信息，会走这个分支
      hilog.info(0x0000, 'testTag', `success to get HomeNavDestination's name: ${info.name}`)
    } else {
      // 变更前无法获取到主页NavDestination的信息，会走这个分支
      hilog.info(0x0000, 'testTag', `failed to get NavDestinationInfo for HomeNavDestination`)
    }
  }

  build() {
    Column() {
      Button('queryOuterNavDestination').onClick(() => {
        this.GetDestInfo();
      })
    }
  }
}

@Component
struct MyHomeDestination {
  GetDestInfo() {
    // 向下查找当前自定义组件内部的NavDestination
    let info = this.queryNavDestinationInfo(true);
    if (info) {
      // 变更后能够获取到主页NavDestination的信息，会走这个分支
      hilog.info(0x0000, 'testTag', `success to get HomeNavDestination's name: ${info.name}`)
    } else {
      // 变更前无法获取到主页NavDestination的信息，会走这个分支
      hilog.info(0x0000, 'testTag', `failed to get NavDestinationInfo for HomeNavDestination`)
    }
  }

  build() {
    NavDestination() {
      Column() {
        Button('queryInnerNavDestination').onClick(() => {
          this.GetDestInfo();
        })
        InnerCustomComponent()
      }
    }
    .width('100%')
    .height('100%')
    .title('HomePage')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  MyPageName(name: string) {
    if (name === 'Home') {
      MyHomeDestination()
    } else {
      MyPage()
    }
  }

  build() {
    // 使用主页NavDestination功能
    Navigation(this.stack, {name: 'Home'}) {
    }
    .width('100%')
    .height('100%')
    .navDestination(this.MyPageName)
  }
}
```

## cl.arkui.4 主页NavDestination的onResult接口行为变更

**访问级别**

公共能力

**变更原因**

主页NavDestination的onResult接口在如下场景中表现不符合预期，具体场景为：开发者使用了主页NavDestination，且操作前栈为PageA（未设置onResult）、PageB。从PageB返回到PageA时，会触发主页NavDestination的onResult，不符合接口设计规格。

**变更影响**

变更前：通过入参包含HomePathInfo的Navigation接口，指定一个NavDestination作为Navigation主页后，栈操作的目标页面非主页面，且没有设置[onResult](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onresult15)，返回该页面时会触发主页NavDestination的onResult。

变更后：栈操作的目标页面非主页面，且没有设置[onResult](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onresult15)，返回该页面时不会触发主页NavDestination的onResult。

**起始 API Level**

20

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

NavDestination的[onResult](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onresult15)接口。

**适配指导**

开发者需要根据变更内容审视自身业务代码是否需要进行适配，下面的示例代码展示了主页NavDestination的onResult接口在如下场景中的变化：使用了主页NavDestination，栈中当前有PageA（未设置onResult）和PageB两个页面，然后从PageB返回到PageA，变更前会触发主页的NavDestination的onResult，变更后不会触发主页NavDestination的onResult。

```ts
import hilog from '@ohos.hilog';

@Component
struct MyPage {
  @State name: string = '';
  build() {
    // PageA不设置onResult事件
    NavDestination() {
    }
    .width('100%')
    .height('100%')
    .title(`${this.name}`)
    .onReady((ctx: NavDestinationContext) => {
      this.name = ctx.pathInfo.name;
    })
  }
}

@Component
struct MyHomeDestination {
  build() {
    NavDestination() {
    }
    .width('100%')
    .height('100%')
    .title('HomePage')
    .onResult((param: ESObject) => {
      // PageA未设置onResult事件，从PageB返回到PageA时，
      // 在变更前会触发主页NavDestination的onResult函数，在变更后不会触发主页NavDestination的onResult函数
      hilog.info(0x0000, 'testTag', `HomeDestination onResult`)
    })
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  MyPageName(name: string) {
    if (name === 'Home') {
      MyHomeDestination()
    } else {
      MyPage()
    }
  }

  aboutToAppear(): void {
    this.stack.pushPath({name: 'PageA'})
    this.stack.pushPath({name: 'PageB'})
  }

  build() {
    // 使用主页NavDestination功能
    Navigation(this.stack, {name: 'Home'}) {
    }
    .width('100%')
    .height('100%')
    .navDestination(this.MyPageName)
  }
}
```

## cl.arkui.5 NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL事件回调的返回值行为变更

**访问级别**

公开接口

**变更原因**

[NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL](../../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)事件回调返回值中的主轴方向上页面的长度ArkUI_NodeComponentEvent.data[3].f32，和实际长度不符。

**变更影响**

此变更涉及应用适配。

- 变更前：NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL的返回值中的ArkUI_NodeComponentEvent.data[3].f32不符合页面的实际主轴长度。例如实际长度为100vp，开发者接收vp单位时，返回的值是100/屏幕像素密度，开发者接收px单位时，返回的值是100。
  
- 变更后：NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL的返回值中的ArkUI_NodeComponentEvent.data[3].f32符合页面的实际主轴长度。例如实际长度为100vp，开发者接收vp单位时，返回的值是100，开发者接收px单位时，返回的值是100*屏幕像素密度。

**起始API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

[NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL](../../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype)的返回参数值ArkUI_NodeComponentEvent.data[3].f32。

**适配指导**

原先的返回值不符合实际页面主轴长度，开发者在使用时需要给获取的返回值*屏幕像素密度。变更后可以直接使用正确的长度值进行业务开发。

```cpp
static ArkUI_NativeNodeAPI_1 *nodeAPI_ = reinterpret_cast<ArkUI_NativeNodeAPI_1 *>(
    OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1"));
const unsigned int LOG_PRINT_DOMAIN = 0xFF00;

static napi_value CreateSwiperNode(napi_env env, napi_callback_info info) {
    const int size = 11;
    const char *arr[size] = {"0", "1", "2", "3"};
    static ArkUI_NodeHandle swiper = nodeAPI_->createNode(ARKUI_NODE_SWIPER);

    for (int j = ConstIde::NUMBER_0; j < size; j++) {
        ArkUI_NodeHandle textNode = nodeAPI_->createNode(ARKUI_NODE_TEXT);
        ArkUI_AttributeItem content = {.string = arr[j]};
        nodeAPI_->setAttribute(textNode, NODE_TEXT_CONTENT, &content);

        ArkUI_NumberValue value[] = {0};
        ArkUI_AttributeItem item = {.value = value, .size = 1};
        value[ConstIde::NUMBER_0].f32 = ConstIde::TEXT_HEIGHT_VP;
        nodeAPI_->setAttribute(textNode, NODE_HEIGHT, &item);
        value[ConstIde::NUMBER_0].u32 = ConstIde::TEXT_BG_COLOR;
        nodeAPI_->setAttribute(textNode, NODE_BACKGROUND_COLOR, &item);
        value[ConstIde::NUMBER_0].i32 = ConstIde::TEXT_ALIGN_CENTER;
        nodeAPI_->setAttribute(textNode, NODE_TEXT_ALIGN, &item);
        value[ConstIde::NUMBER_0].f32 = ConstIde::TEXT_FONT_SIZE_VP;
        nodeAPI_->setAttribute(textNode, NODE_FONT_SIZE, &item);

        ArkUI_AttributeItem textId = {.string = "SwiperAutoPlayText"};
        nodeAPI_->setAttribute(textNode, NODE_ID, &textId);
        nodeAPI_->addChild(swiper, textNode);
    }
    ArkUI_NumberValue value[] = {};
    ArkUI_AttributeItem item = {.value = value, .size = 1};
    
    value[0].f32 = 300;
    nodeAPI_->setAttribute(swiper, NODE_WIDTH, &item);

    nodeAPI_->setLengthMetricUnit(swiper, ArkUI_LengthMetricUnit::ARKUI_LENGTH_METRIC_UNIT_PX);
    nodeAPI_->registerNodeEvent(swiper, NODE_SWIPER_EVENT_ON_CONTENT_DID_SCROLL, 0, nullptr);
    nodeAPI_->addNodeEventReceiver(swiper, [](ArkUI_NodeEvent *event) {
        ArkUI_NodeComponentEvent* compEvent = OH_ArkUI_NodeEvent_GetNodeComponentEvent(event) ; 
        int selectedIndex = compEvent->data[0].i32; 
        int index = compEvent->data[1].i32;
        float position = compEvent->data[2].f32; 
        float maxAxisLength = compEvent->data[3].f32;
        // 变更前页面真实的长度为maxAxisLength * 屏幕像素密度，变更后为maxAxisLength
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, "Manager", "maxAxisLength: %{public}f", maxAxisLength);
    });
}
```