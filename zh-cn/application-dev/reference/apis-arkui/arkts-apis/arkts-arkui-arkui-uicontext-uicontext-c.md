# UIContext

UIContext实例对象。

> **说明：**

> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。
> 
> - 以下API需要通过对应的UIContext实例调用。获取UIContext分为三种方式，第一种是使用ohos.window中的
> getUIContext()方法获取UIContext实例，第二种是通过自定
> 义组件内置方法getUIContext()获取UIContext
> 实例，第三种是通过UIContext类的静态方法如[getCallingScopeUIContext](#getcallingscopeuicontext)获取UIContext实例。本文中
> UIContext对象以uiContext表示。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## addLocalInputEventMonitor

```TypeScript
addLocalInputEventMonitor(eventMask: number, listener: InputEventListener): InputEventMonitor
```

注册本地输入事件监视器。接口名中的“Local”表示监视器只在当前UIContext内有效。 并且不影响其他UIContext实例。每个UIContext都维护自己独立的监视器列表。

> **说明：**
>&gt;性能警告：不要在回调中执行耗时操作！
>&gt;监控对象注释：
> 
> 
> -返回的Monitor对象是系统创建的唯一标识符。
> 
> 
> -开发人员不能主动构造或伪造此对象。
> 
> 
> -必须保存返回的监控对象引用，以便后续取消。
> 
> 
> -建议使用变量来保存，以免丢失引用。
>&gt;使用示例：
>&gt;。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventMask | number | 是 | 事件类型掩码，指定要监视的事件类型 位运算。 取值限定为整数。 |
| listener | InputEventListener | 是 | 事件监听器回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputEventMonitor](../arkts-components/arkts-arkui-inputeventmonitor-i.md) | Unique identifier object for the monitor, used for subsequent cancellation of registration. |

**示例**

```TypeScript
@Entry
@Component
struct InputEventMonitorSample {
  private uiContext: UIContext | undefined = undefined;
  private monitor: InputEventMonitor | null = null;
  aboutToAppear() {
    this.uiContext = this.getUIContext();
    // 监听鼠标左键按下事件
    this.monitor = this.uiContext.addLocalInputEventMonitor(
      InputEventSubTypeMask.LEFT_MOUSE_DOWN,
      (wrapper: RawInputEventWrapper) => {
        if (wrapper.isMouseEvent()) {
          const event = wrapper.asMouseEvent()!;
          console.info(`Mouse down at (${event.windowX}, ${event.windowY})`);
          return { action: InputEventInterceptAction.CONTINUE };  // 允许事件继续传递
        }
        return { action: InputEventInterceptAction.BLOCK };  // 阻止事件传递
      }
    );
  }
  aboutToDisappear() {
    if (this.monitor && this.uiContext) {
      this.uiContext.removeLocalInputEventMonitor(this.monitor);
    }
  }
  build() {
    Column() {
      Text('Input Event Monitor Sample')
        .fontSize(20)
        .margin(20)
    }
    .width('100%')
    .height('100%')
  }
}
```

## animateTo

```TypeScript
animateTo(value: AnimateParam, event: () => void): void
```

提供animateTo接口，用于为闭包代码中的状态变化添加过渡动画效果。

> **说明：**
> 
> - 不推荐在aboutToAppear、aboutToDisappear中调用动画。
> 
> - 如果在aboutToAppear中调用动
> 画，自定义组件内的build还未执行，内部组件还未创建，动画时机过早，动画属性没有初值无法对组件产生动画。
> 
> - 执行aboutToDisappear
> 时，组件即将销毁，不能在aboutToDisappear里面做动画。
> 
> - 在组件出现和消失时，可以通过组件内转场添加动画效果。
> 
> - 组件内转场不支持的属性，可以参考显式动画中的
> 示例2，使用animateTo实现动画执行结束后组件消失的效
> 果。
> 
> - 某些场景下，在[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中使用animateTo动画，会产生异常效果，
> 具体可参考：[在状态管理V2中使用animateTo动画效果异常](../../../ui/state-management/arkts-new-local.md#在状态管理v2中使用animateto动画效果异常)。
> 
> - UIAbility从前台切换至后台时会立即结束仍在步进中的有限循环动画，从而触发动画播放完成回调[onFinish](../arkts-components/arkts-arkui-animateparam-i.md)。
> 
> - 在设置的开发者选项中关闭过渡动画，动画会当帧结束，onFinish动画播放完成回调会立即执行，请避免在回调中加入时序相关的功能逻辑。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | 是 | 设置动画效果相关参数。 |
| event | () =&gt; void | 是 | 指定显示动效的闭包函数，在闭包函数中导致的状态变化系统会自动插入过渡动画。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct AnimateToExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State rotateAngle: number = 0;
  private flag: boolean = true;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext();
    if (!this.uiContext) {
      console.warn("no uiContext");
      return;
    }
  }

  build() {
    Column() {
      Button('change size')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            this.uiContext?.animateTo({
              duration: 2000,
              curve: Curve.EaseOut,
              iterations: 3,
              playMode: PlayMode.Normal,
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.widthSize = 150;
              this.heightSize = 60;
            });
          } else {
            this.uiContext?.animateTo({}, () => {
              this.widthSize = 250;
              this.heightSize = 100;
            });
          }
          this.flag = !this.flag;
        })
      Button('stop rotating')
        .margin(50)
        .rotate({ x: 0, y: 0, z: 1, angle: this.rotateAngle })
        .onAppear(() => {
          // 组件出现时开始做动画
          this.uiContext?.animateTo({
            duration: 1200,
            curve: Curve.Friction,
            delay: 500,
            iterations: -1, // 设置-1表示动画无限循环
            playMode: PlayMode.Alternate,
            expectedFrameRateRange: {
              min: 10,
              max: 120,
              expected: 60,
            }
          }, () => {
            this.rotateAngle = 90
          });
        })
        .onClick(() => {
          this.uiContext?.animateTo({ duration: 0 }, () => {
            // this.rotateAngle之前为90，在duration为0的动画中修改属性，可以停止该属性之前的动画，按新设置的属性显示
            this.rotateAngle = 0;
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## animateToImmediately

```TypeScript
animateToImmediately(param: AnimateParam, processor: Callback<void>): void
```

通过UIContext对象指定明确的动画主实例上下文，并触发显式动画立即下发。避免由于找不到实例或实例不对，导致的动画不执行或动画结束回调不执行问题。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | 是 | 设置动画效果相关参数。 |
| processor | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。指定显示动效的闭包函数，在闭包函数中导致的状态变化系统会自动插入过渡动画。 |

**示例**

该示例通过UIContext对象获取显式立即动画，并调用animateToImmediately接口实现参数定义的动画效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct AnimateToImmediatelyExample {
  @State widthSize: number = 250
  @State heightSize: number = 100
  @State opacitySize: number = 0
  private flag: boolean = true
  uiContext: UIContext | null | undefined = this.getUIContext();

  build() {
    Column() {
      Column()
        .width(this.widthSize)
        .height(this.heightSize)
        .backgroundColor(Color.Green)
        .opacity(this.opacitySize)
      Button('change size')
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            this.uiContext?.animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.opacitySize = 1
            })
            this.uiContext?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.widthSize = 150
              this.heightSize = 60
            })
          } else {
            this.uiContext?.animateToImmediately({
              delay: 0,
              duration: 1000
            }, () => {
              this.widthSize = 250
              this.heightSize = 100
            })
            this.uiContext?.animateTo({
              delay: 1000,
              duration: 1000
            }, () => {
              this.opacitySize = 0
            })
          }
          this.flag = !this.flag
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## bindTabsToNestedScrollable

```TypeScript
bindTabsToNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Bind tabs to nested scrollable container components to automatically hide tab bar.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | 是 | The controller of the tabs. |
| parentScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | 是 | The controller of the parent scrollable container component. |
| childScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | 是 | The controller of the child scrollable container component. |

**示例**

参考[bindTabsToScrollable](#bindtabstoscrollable)接口示例。

## bindTabsToScrollable

```TypeScript
bindTabsToScrollable(tabsController: TabsController, scroller: Scroller): void
```

Bind tabs to scrollable container component to automatically hide tab bar.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | 是 | The controller of the tabs. |
| scroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | 是 | The controller of the scrollable container component. |

**示例**

```TypeScript
@Entry
@Component
struct TabsExample {
  private arr: string[] = [];
  private parentTabsController: TabsController = new TabsController();
  private childTabsController: TabsController = new TabsController();
  private listScroller: Scroller = new Scroller();
  private parentScroller: Scroller = new Scroller();
  private childScroller: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 20; i++) {
      this.arr.push(i.toString());
    }
    let context = this.getUIContext();
    context.bindTabsToScrollable(this.parentTabsController, this.listScroller);
    context.bindTabsToScrollable(this.childTabsController, this.listScroller);
    context.bindTabsToNestedScrollable(this.parentTabsController, this.parentScroller, this.childScroller);
  }

  aboutToDisappear(): void {
    let context = this.getUIContext();
    context.unbindTabsFromScrollable(this.parentTabsController, this.listScroller);
    context.unbindTabsFromScrollable(this.childTabsController, this.listScroller);
    context.unbindTabsFromNestedScrollable(this.parentTabsController, this.parentScroller, this.childScroller);
  }

  build() {
    Tabs({ barPosition: BarPosition.End, controller: this.parentTabsController }) {
      TabContent() {
        Tabs({ controller: this.childTabsController }) {
          TabContent() {
            List({ space: 20, initialIndex: 0, scroller: this.listScroller }) {
              ForEach(this.arr, (item: string) => {
                ListItem() {
                  Text(item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Gray)
                }
              }, (item: string) => item)
            }
            .scrollBar(BarState.Off)
            .width('90%')
            .height('100%')
            .contentStartOffset(56)
            .contentEndOffset(52)
          }.tabBar(SubTabBarStyle.of('顶部页签'))
        }
        .width('100%')
        .height('100%')
        .barOverlap(true) // 使TabBar叠加在TabContent上，当TabBar向上或向下隐藏后，原位置处不为空白
        .clip(true) // 对超出Tabs组件范围的子组件进行裁剪，防止TabBar向上或向下隐藏后误触TabBar
      }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'scroller联动多个TabsController'))

      TabContent() {
        Scroll(this.parentScroller) {
            List({ space: 20, initialIndex: 0, scroller: this.childScroller }) {
              ForEach(this.arr, (item: string) => {
                ListItem() {
                  Text(item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Gray)
                }
              }, (item: string) => item)
            }
            .scrollBar(BarState.Off)
            .width('90%')
            .height('100%')
            .contentEndOffset(52)
            .nestedScroll({ scrollForward: NestedScrollMode.SELF_FIRST, scrollBackward: NestedScrollMode.SELF_FIRST })
        }
        .width('100%')
        .height('100%')
        .scrollBar(BarState.Off)
        .scrollable(ScrollDirection.Vertical)
        .edgeEffect(EdgeEffect.Spring)
      }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), '嵌套的scroller联动TabsController'))
    }
    .width('100%')
    .height('100%')
    .barOverlap(true) // 使TabBar叠加在TabContent上，当TabBar向上或向下隐藏后，原位置处不为空白
    .clip(true) // 对超出Tabs组件范围的子组件进行裁剪，防止TabBar向上或向下隐藏后误触TabBar
  }
}
```

## closeBindSheet

```TypeScript
closeBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>): Promise<void>
```

关闭bindSheetContent对应的半模态页面，使用Promise异步回调。

> **说明：**
> 
> 使用此接口关闭半模态页面时，不会触发shouldDismiss回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | 是 | 半模态页面中显示的组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-内容节点对应半模态页面错误) | The bindSheetContent is incorrect. |
| [120003](../errorcode-bindSheet.md#120003-无法找到内容节点对应的半模态页面) | The bindSheetContent cannot be found. |

**示例**

```TypeScript
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.error('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## constructor

```TypeScript
constructor()
```

构造UIContext对象。

> **说明：**
> 
> 通过构造函数创建的UIContext对象指向不明确的UI上下文，即不指向任何UI实例。该UIContext对应实例的唯一标识ID为-1。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

function getUIContextByAtomicInterface(): UIContext {
  let callingScopeUIContext = UIContext.getCallingScopeUIContext();
  if (callingScopeUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of calling scope.`)
    return callingScopeUIContext;
  }
  let allContexts = UIContext.getAllUIContexts();
  let length = allContexts.length;
  if (length === 1) {
    hilog.info(0x00, 'testTag', `Get UIContext of unique UI instance.`)
    return allContexts[0];
  }
  let lastFocusedUIContext = UIContext.getLastFocusedUIContext();
  if (lastFocusedUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of last focused instance.`)
    return lastFocusedUIContext;
  }
  let lastForegroundUIContext = UIContext.getLastForegroundUIContext();
  if (lastForegroundUIContext) {
    hilog.info(0x00, 'testTag', `Get UIContext of last foregrounded instance.`)
    return lastForegroundUIContext;
  }
  if (length !== 0) {
    hilog.info(0x00, 'testTag', `Get UIContext with maximum instanceId.`)
    return allContexts[length - 1];
  }
  hilog.info(0x00, 'testTag', `Get UIContext of undefined calling scope.`)
  return new UIContext();
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    let uiContext = this.getUIContext();
    hilog.info(0x00, 'testTag', `aboutToAppear UIContext: ${uiContext.getId()}`)
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let resolvedUIContext = UIContext.resolveUIContext();
          let contextByAtomicInterface = getUIContextByAtomicInterface();
          hilog.info(0x00, 'testTag',
            `UIContext id: ${resolvedUIContext.getId()}, strategy: ${resolvedUIContext.strategy}, contextByAtomicInterface: ${contextByAtomicInterface.getId()}`);
          this.message = 'Welcome';
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions): AnimatorResult
```

定义Animator类。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 定义动画选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator结果接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { AnimatorOptions, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // 创建主窗口，设置此功能的主页
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', err.message);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      let uiContext = windowStage.getMainWindowSync().getUIContext();
      let options:AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 3,
        begin: 200.0,
        end: 400.0
      };
      uiContext.createAnimator(options);
    });
  }
}
```

## createAnimator

```TypeScript
createAnimator(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

创建animator动画结果对象（AnimatorResult）。与[createAnimator](#createanimator)相比，新增对 [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md)类型入参的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) \| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 是 | 定义动画选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator结果接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { SimpleAnimatorOptions, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // 创建主窗口，设置此功能的主页
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', err.message);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      let uiContext = windowStage.getMainWindowSync().getUIContext();
      let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(2000);
      uiContext.createAnimator(options);
    });
  }
}
```

## createUIContextWithoutWindow

```TypeScript
static createUIContextWithoutWindow(context: common.UIAbilityContext | common.ExtensionContext) : UIContext | undefined
```

创建一个不依赖窗口的UI实例，并返回其UI上下文。该接口所创建的UI实例是单例。

> **说明：**
> 
> 返回的UI上下文只可用于创建[自定义节点](../../../ui/arkts-user-defined-node.md)，不能执行其他UI操作。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.UIAbilityContext \| common.ExtensionContext | 是 | [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)或 ExtensionAbility所对应的上下文环境。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) \| undefined | Context of the created UI instance, or **undefined** if creation fails. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. The number of parameters is incorrect.   2. Invalid parameter type of context. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例**

```TypeScript
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let uiContext: UIContext | undefined = UIContext.createUIContextWithoutWindow(this.context);
  }

  // ......
}
```

## destroyUIContextWithoutWindow

```TypeScript
static destroyUIContextWithoutWindow(): void
```

销毁[createUIContextWithoutWindow](#createuicontextwithoutwindow)创建的UI实例。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let uiContext: UIContext | undefined = UIContext.createUIContextWithoutWindow(this.context);
    UIContext.destroyUIContextWithoutWindow();
  }

  // ......
}
```

## dispatchKeyEvent

```TypeScript
dispatchKeyEvent(node: number | string, event: KeyEvent): boolean
```

Dispach keyboard event to the frameNode with inspector key.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | number \| string | 是 | The uniqueId or inspector key of the target FrameNode. |
| event | KeyEvent | 是 | The keyboard event. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns whether the key event is consumed. |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      Row() {
        Button('Button1').id('Button1').onKeyEvent((event) => {
          console.info("Button1");
          return true;
        })
        Button('Button2').id('Button2').onKeyEvent((event) => {
          console.info("Button2");
          return true;
        })
      }
      .width('100%')
      .height('100%')
      .id('Row1')
      .onKeyEventDispatch((event) => {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Button1');
        return context.dispatchKeyEvent('Button1', event);
      })

    }
    .height('100%')
    .width('100%')
    .onKeyEventDispatch((event) => {
      if (event.type == KeyType.Down) {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Row1');
        return context.dispatchKeyEvent('Row1', event);
      }
      return true;
    })
  }
}
```

## enableEventPassthrough

```TypeScript
enableEventPassthrough(enabled: boolean, eventType: RawInputEventType): void
```

是否启用或禁用事件直通。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 启用或禁用事件透传。默认值为false。 |
| eventType | [RawInputEventType](arkts-arkui-rawinputeventtype-e.md) | 是 | 原始输入事件的类型。 |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Enable Event Passthrough')
        .onClick(() => {
          this.getUIContext()?.enableEventPassthrough(true, RawInputEventType.TOUCH);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## enableSwipeBack

```TypeScript
enableSwipeBack(enabled: Optional<boolean>): void
```

whether to enable or disable swipe to back event.

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | enable or disable swipe to back event. |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  @State isEnable: boolean = true;

  build() {
    RelativeContainer() {
      Button(`enable swipe back: ${this.isEnable}`).onClick(() => {
        this.isEnable = !this.isEnable;
        this.getUIContext().enableSwipeBack(this.isEnable);
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

## fp2px

```TypeScript
fp2px(value: number): number
```

将fp单位的数值转换为以px为单位的数值。转换公式为：px值 = fp值 × 像素密度 × 字体缩放比例像素密度：当前窗口生效的像素密度值，即虚拟屏幕的密度[VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md).density。字体缩放比例：系统设置的字体缩放系数，对应 Configuration.fontScale。

> **说明：**
> 
> getUIContext需在windowStage.
> [loadContent](arkts-arkui-window-window-i.md#loadcontent)之后调用，确保UIContext初始化完成后
> 调用此接口，否则无法返回准确结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的数值。 |

**示例**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().fp2px(50),
          centerY: this.getUIContext().fp2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## getAllUIContexts

```TypeScript
static getAllUIContexts(): UIContext[]
```

获取所有当前有效的UIContext实例。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)[] | Array of all currently valid UIContext instances. Returns an empty array if no valid UIContext instance exists. |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContexts = UIContext.getAllUIContexts();
          hilog.info(0x00, 'testTag', `There are ${uiContexts.length} UIContext(s)`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getAtomicServiceBar

```TypeScript
getAtomicServiceBar(): Nullable<AtomicServiceBar>
```

Get AtomicServiceBar.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Nullable](arkts-arkui-nullable-t.md)&lt;[AtomicServiceBar](arkts-arkui-arkui-uicontext-atomicservicebar-i.md)&gt; | The atomic service bar. |

**示例**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    console.info('Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        console.info('Get AtomServiceBar Successfully.');
      } else {
        console.error('Get AtomicServiceBar failed.');
      }
    });
  }
}
```

## getAttachedFrameNodeById

```TypeScript
getAttachedFrameNodeById(id: string): FrameNode | null
```

通过组件的id获取当前窗口上的实体节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 节点对应的组件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | The instance of FrameNode. |

**示例**

```TypeScript
@Entry
@Component
struct MyComponent {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let node = this.getUIContext().getAttachedFrameNodeById("HelloWorld");
          console.info(`Find HelloWorld Tag:${node!.getNodeType()} id:${node!.getUniqueId()}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getCallingScopeUIContext

```TypeScript
static getCallingScopeUIContext(): UIContext | undefined
```

获取当前[调用作用域](../../../ui/arkts-global-interface.md#基本概念)的UIContext，调用作用域不明确时返回undefined。

> **说明：**
> 
> 返回的UIContext对象可能指向一个已销毁的UI实例，通常在由已销毁的实例抛出异步任务时出现。建议通过[isAvailable](#isavailable)接口判断其有效性。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) \| undefined | UIContext of the current calling scope. Returns **undefined** if the calling scope is ambiguous. |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContext = UIContext.getCallingScopeUIContext();
          hilog.info(0x00, 'testTag', 'Current calling UIContext is : ' + uiContext?.isAvailable());
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getComponentSnapshot

```TypeScript
getComponentSnapshot(): ComponentSnapshot
```

获取组件快照。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md) | 组件快照。 |

**示例**

完整示例请参考ComponentSnapshot中的示例。

## getComponentUtils

```TypeScript
getComponentUtils(): ComponentUtils
```

get object ComponentUtils.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ComponentUtils](arkts-arkui-arkui-uicontext-componentutils-c.md) | object ComponentUtils. |

**示例**

完整示例请参考示例1（获取ComponentUtils对象）。

## getContextMenuController

```TypeScript
getContextMenuController(): ContextMenuController
```

Get object context menu controller.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuController](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md) | object context menu controller. |

## getCursorController

```TypeScript
getCursorController(): CursorController
```

Get object cursor controller.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CursorController](arkts-arkui-arkui-uicontext-cursorcontroller-c.md) | object cursor controller. |

**示例**

完整示例请参考CursorController中的示例。

## getDialogPresenter

```TypeScript
getDialogPresenter(): DialogPresenter
```

获取Dialog对象。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DialogPresenter](arkts-arkui-arkui-uicontext-dialogpresenter-c.md) | Dialog对象。 |

**示例**

完整示例请参考DialogPresenter中的示例。

## getDragController

```TypeScript
getDragController(): DragController
```

Get DragController.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md) | the DragController |

**示例**

完整示例请参考DragController中的示例。

## getFilteredInspectorTree

```TypeScript
getFilteredInspectorTree(filters?: Array<string>): string
```

get the filtered attributes of the component tree.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filters | Array &lt;string&gt; | 否 | List of component attributes used for filtering. Currently, only the following filter fields are supported:    **"id"**: unique ID of the component.    **"src"**: source of the resource.    **"content"**: information or data contained in the element, component, or object.    **"editable"**: whether the component is editable.    **"scrollable"**: whether the component is scrollable.    **"selectable"**: whether the component is selectable.    **"focusable"**: whether the component is focusable.    **"focused"**: whether the component is currently focused. If **filters** includes one or more fields, unspecified fields will be filtered out from the results. If **filters** is not provided or is an empty array, none of the aforementioned fields will be filtered out. The following filter field is supported since API version 20:    **"isLayoutInspector"**: whether the component tree contains custom components. If **filters** is omitted or does not contain **"isLayoutInspector"**, the returned component tree will not include custom component details. Other filter fields are used only in testing scenarios. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | JSON string of the component tree and component attributes. For details about each field in the component, see the return value description of [getInspectorInfo]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
uiContext.getFilteredInspectorTree(['id', 'src', 'content']);
```

```TypeScript
// xxx.ets
import { UIContext } from '@kit.ArkUI';
@Entry
@Component
struct ComponentPage {
  loopConsole(inspectorStr: string, i: string) {
    console.info(`InsTree ${i}| type: ${JSON.parse(inspectorStr).$type}, ID: ${JSON.parse(inspectorStr).$ID}`);
    if (JSON.parse(inspectorStr).$children) {
      i += '-';
      for (let index = 0; index < JSON.parse(inspectorStr).$children.length; index++) {
        this.loopConsole(JSON.stringify(JSON.parse(inspectorStr).$children[index]), i);
      }
    }
  }

  build() {
    Column() {
      Button('content').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        let inspectorStr = uiContext.getFilteredInspectorTree(['content']);
        console.info(`InsTree : ${inspectorStr}`);
        inspectorStr = JSON.stringify(JSON.parse(inspectorStr));
        this.loopConsole(inspectorStr, '-');
      })
      Button('isLayoutInspector').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        let inspectorStr = uiContext.getFilteredInspectorTree(['isLayoutInspector']);
        console.info(`InsTree : ${inspectorStr}`);
        inspectorStr = JSON.stringify(JSON.parse(inspectorStr).content);
        this.loopConsole(inspectorStr, '-');
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

当传入"content"过滤字段时，返回的JSON字符串结构如下：

```TypeScript
InsTree : {"$type":"root","width":"720.000000","height":"1280.000000","$resolution":"1.500000","$children":[{"$type":"Column","$ID":15,"type":"build-in","$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"","$attrs":{},"$children":[{"$type":"Button","$ID":16,"type":"build-in","$rect":"[293.00, 72.00],[427.00,132.00]","$debugLine":"","$attrs":{}},{"$type":"Button","$ID":18,"type":"build-in","$rect":"[237.00, 132.00],[484.00,192.00]","$debugLine":"","$attrs":{}}]}]}\
InsTree -| type: root, ID: undefined
InsTree --| type: Column, ID: 15
InsTree ---| type: Button, ID: 16
InsTree ---| type: Button, ID: 18
```

从API version 20开始，当传入"isLayoutInspector"过滤字段时，返回的JSON字符串结构新增外层结构"type"与"content"，其中"content"包含未增加该字段时的原有JSON字符串结构；同时，返回值结构中增添自定义组件。返回的JSON字符串结构如下：

```TypeScript
InsTree : {"type":"root","content":{"$type":"root","width":"720.000000","height":"1280.000000","$resolution":"1.500000","$children":[{"$type":"JsView","$ID":13,"type":"custom","state":{"observedPropertiesInfo":[],"viewInfo":{"componentName":"ComponentPage","id":14,"isV2":false,"isViewActive_":true}},"$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"{\"$line\":\"(0:0)\"}","viewTag":"ComponentPage","$attrs":{"viewKey":"13"},"$children":[{"$type":"Column","$ID":15, "type":"build-in","$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"","$attrs":{ ...
InsTree -| type: root, ID: undefined
InsTree --| type: JsView, ID: 13
InsTree ---| type: Column, ID: 15
InsTree ----| type: Button, ID: 16
InsTree ----| type: Button, ID: 18
```

## getFilteredInspectorTreeById

```TypeScript
getFilteredInspectorTreeById(id: string, depth: number, filters?: Array<string>): string
```

get the filtered attributes of the component tree with the specified id and depth

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | ID of the target component. |
| depth | number | 是 | Number of layers of child components. If the value is **0**, the attributes of the specified component and all its child components are obtained. If the value is **1**, only the attributes of the specified component are obtained. If the value is **2**, the attributes of the specified component and its level-1 child components are obtained. The rest can be deduced by analogy. |
| filters | Array &lt;string&gt; | 否 | List of component attributes used for filtering. Currently, only the following filter fields are supported:    **"id"**: unique ID of the component.    **"src"**: source of the resource.    **"content"**: information or data contained in the element, component, or object.    **"editable"**: whether the component is editable.    **"scrollable"**: whether the component is scrollable.    **"selectable"**: whether the component is selectable.    **"focusable"**: whether the component is focusable.    **"focused"**: whether the component is currently focused. If **filters** includes one or more fields, unspecified fields will be filtered out from the results. If **filters** is not provided or is an empty array, none of the aforementioned fields will be filtered out. Other filter fields are used only in testing scenarios. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | JSON string of the attributes of the specified component and its child components. For details about each field in the component, see the return value |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
uiContext.getFilteredInspectorTreeById('testId', 0, ['id', 'src', 'content']);
```

```TypeScript
import { UIContext } from '@kit.ArkUI';
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text("Hello World")
        .fontSize(20)
        .id("TEXT")
      Button('getFilteredInspectorTreeById').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        try {
          let inspectorStr = uiContext.getFilteredInspectorTreeById('TEXT', 1, ["id", "src"]);
          console.info(`result1: ${inspectorStr}`);
          inspectorStr = JSON.stringify(JSON.parse(inspectorStr)['$children'][0]);
          console.info(`result2: ${inspectorStr}`);
          inspectorStr = uiContext.getFilteredInspectorTreeById('TEXT', 1, ["src"]);
          inspectorStr = JSON.stringify(JSON.parse(inspectorStr)['$children'][0]);
          console.info(`result3: ${inspectorStr}`);
        } catch(e) {
          console.error(`getFilteredInspectorTreeById error: ${e}`);
        }
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

返回的JSON字符串结构如下：

```TypeScript
result1: {"$type":"root","width":"1260.000000","height":"2720.000000","$resolution":"3.250000","$children":[{"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"id":"TEXT","isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}]}
result2: {"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"id":"TEXT","isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}
result3: {"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}
```

## getFocusController

```TypeScript
getFocusController(): FocusController
```

获取焦点控制器。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FocusController](arkts-arkui-arkui-uicontext-focuscontroller-c.md) | 焦点控制器 |

**示例**

完整示例请参考FocusController中的示例。

## getFont

```TypeScript
getFont(): Font
```

获取Font对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Font](arkts-arkui-arkui-uicontext-font-c.md) | Font实例对象。 |

**示例**

完整示例请参考Font中的示例。

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

通过组件的id获取组件树的实体节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 节点对应的组件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | The instance of FrameNode. |

**示例**

完整示例请参考获取根节点示例。

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

通过组件的uniqueId获取组件树的实体节点。
1. 当uniqueId对应的是系统组件时，返回组件所对应的FrameNode；
2. 当uniqueId对应的是自定义组件时：  
- 若其有渲染内容，且没有被[@Reusable装饰器](../../../ui/state-management/arkts-reusable.md)修饰时，返回该自定义组件的根节点，类型为__Common__。  
- 若其无渲染内容，或者被[@Reusable装饰器](../../../ui/state-management/arkts-reusable.md)修饰时，在该自定义组件的子组件创建完成前调用此接口，将返回null；在该自定义组件的子组件创建完成后调用，返回其第一个子组件的FrameNode。  
3. 当uniqueId无对应的组件时，返回null。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 节点对应的UniqueId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | The FrameNode with the target uniqueId, or null if the frameNode is not existed. |

**示例**

```TypeScript
import { UIContext, FrameNode } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let uniqueId: number = this.getUniqueId();
    let uiContext: UIContext = this.getUIContext();
    if (uiContext) {
      let node: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
    }
  }

  build() {
    // ...
  }
}
```

## getHostContext

```TypeScript
getHostContext(): Context | undefined
```

获得当前元能力的Context。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](arkts-arkui-context-t.md) \| undefined | Context of the ability. The context type depends on the ability type. For example, if this API is called in a page within a UIAbility window, the returned context type is [UIAbilityContext]{ |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  uiContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Text("cacheDir='" + this.uiContext?.getHostContext()?.cacheDir + "'")
          .fontSize(25)
          .border({ color: Color.Red, width: 2 })
          .padding(50)
        Text("bundleCodeDir='" + this.uiContext?.getHostContext()?.bundleCodeDir + "'")
          .fontSize(25)
          .border({ color: Color.Red, width: 2 })
          .padding(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getId

```TypeScript
getId(): number
```

获取UI实例对象唯一标识，多实例场景下，开发者可使用此唯一标识区分多个UI实例对象，便于管理。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 后端实例的唯一标识。取值范围为[-1, +∞)。 |

**示例**

```TypeScript
@Entry
@Component
struct Index{
  build(){
    Column()
      .width("100%")
      .height("100%")
      .onClick(() => {
      console.info(`id:${this.getUIContext()?.getId()}`);
    })
  }
}
```

## getKeyboardAvoidMode

```TypeScript
getKeyboardAvoidMode(): KeyboardAvoidMode
```

返回虚拟键盘抬起时页面的避让模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | 返回虚拟键盘抬起时的页面避让模式。 |

**示例**

完整示例请参考示例4（设置键盘避让模式为压缩）、示例5（设置键盘避让模式为上抬）以及示例6（切换避让模式）。

```TypeScript
// EntryAbility.ets
import { KeyboardAvoidMode, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {

      windowStage.loadContent('pages/Index', (err, data) => {
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        let currentKeyboardAvoidMode = uiContext.getKeyboardAvoidMode();
        console.info("KeyboardAvoidMode:", JSON.stringify(currentKeyboardAvoidMode));
      });
    }
}
```

## getLastFocusedUIContext

```TypeScript
static getLastFocusedUIContext(): UIContext | undefined
```

获取最近一次切换到获焦状态的UI实例的UIContext。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) \| undefined | UIContext of the UI instance that most recently switched to the focused state. Returns **undefined** if the most recently focused instance has been destroyed or if no instance has ever been focused. |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContext = UIContext.getLastFocusedUIContext();
          hilog.info(0x00, 'testTag', 'Current calling UIContext is : ' + uiContext?.isAvailable());
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getLastForegroundUIContext

```TypeScript
static getLastForegroundUIContext(): UIContext | undefined
```

获取最近一次切换到前台状态的UI实例的UIContext。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) \| undefined | UIContext of the UI instance that most recently switched to the foreground state. Returns **undefined** if the most recently foreground UI instance has been destroyed or if no UI instance has ever been in the foreground. |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let uiContext = UIContext.getLastForegroundUIContext();
          hilog.info(0x00, 'testTag', 'Current calling UIContext is : ' + uiContext?.isAvailable());
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## getMagnifier

```TypeScript
getMagnifier(): Magnifier
```

获取[Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md)对象，可控制放大镜显示和隐藏。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Magnifier](arkts-arkui-arkui-uicontext-magnifier-c.md) | Magnifier对象，可用于控制放大镜的显示和隐藏。 |

**示例**

参考Magnifier的bind接口示例。

## getMaxFontScale

```TypeScript
getMaxFontScale(): number
```

Get the max font scale.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | The max font scale. |

**示例**

参考[configuration标签](../../../quick-start/app-configuration-file.md#configuration标签)，配置fontSizeMaxScale的值为“1.75”。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('getMaxFontScale').onClick(() => {
        console.info('getMaxFontScale', this.getUIContext().getMaxFontScale().toFixed(2));
      });
    }
  }
}
```

## getMeasureUtils

```TypeScript
getMeasureUtils(): MeasureUtils
```

允许用户通过UIContext对象，获取MeasureUtils对象进行文本计算。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MeasureUtils](arkts-arkui-arkui-uicontext-measureutils-c.md) | 提供文本宽度、高度等相关计算。 |

**示例**

完整示例请参考MeasureUtils中的示例。

## getMediaQuery

```TypeScript
getMediaQuery(): MediaQuery
```

get object mediaQuery.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaQuery](arkts-arkui-arkui-uicontext-mediaquery-c.md) | object MediaQuery. |

**示例**

完整示例请参考mediaquery示例。

## getNavigationInfoByUniqueId

```TypeScript
getNavigationInfoByUniqueId(id: number): observer.NavigationInfo | undefined
```

Get navigation information of the frameNode with uniqueId.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | The uniqueId of the target FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| observer.NavigationInfo \| undefined | The navigation information of the frameNode with the target uniqueId, or undefined if the frameNode is not existed or does not have navigation information. |

**示例**

请参考[getPageInfoByUniqueId](#getpageinfobyuniqueid)的示例。

## getOverlayManager

```TypeScript
getOverlayManager(): OverlayManager
```

Obtains the OverlayManager object.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OverlayManager](arkts-arkui-arkui-uicontext-overlaymanager-c.md) | OverlayManager instance obtained. |

**示例**

完整示例请参考OverlayManager中的示例。

## getOverlayManagerOptions

```TypeScript
getOverlayManagerOptions(): OverlayManagerOptions
```

Get object OverlayManagerOptions.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | object OverlayManagerOptions. |

**示例**

完整示例请参考OverlayManager中的示例。

## getPageInfoByUniqueId

```TypeScript
getPageInfoByUniqueId(id: number): PageInfo
```

通过组件的uniqueId获取该节点对应的Router和NavDestination页面信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | The uniqueId of the target FrameNode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PageInfo](arkts-arkui-arkui-uicontext-pageinfo-i.md) | The page information of the frameNode with the target uniqueId, includes navDestination and router page information. If the frame node does not have navDestination and router page information, it will return an empty object. |

**示例**

```TypeScript
import { UIContext, PageInfo } from '@kit.ArkUI';

@Entry
@Component
struct PageInfoExample {
  @Provide('pageInfos') pageInfos: NavPathStack = new NavPathStack();

  build() {
    Column() {
      Navigation(this.pageInfos) {
        NavDestination() {
          MyComponent()
        }
      }.id('navigation')
    }
  }
}

@Component
struct MyComponent {
  @State content: string = '';

  build() {
    Column() {
      Text('PageInfoExample')
      Button('click').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        const uniqueId: number = this.getUniqueId();
        const pageInfo: PageInfo = uiContext.getPageInfoByUniqueId(uniqueId);
        console.info('pageInfo: ' + JSON.stringify(pageInfo));
        console.info('navigationInfo: ' + JSON.stringify(uiContext.getNavigationInfoByUniqueId(uniqueId)));
      })
      TextArea({
        text: this.content
      })
      .width('100%')
      .height(100)
    }
    .width('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

## getPageRootNode

```TypeScript
getPageRootNode(): FrameNode | null
```

获取UIContext对应页面的根节点。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | FrameNode of the root node of the page or **null**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [120007](../errorcode-uicontext.md#120007-实例不存在) | The UIContext is not available. |

**示例**

```TypeScript
@Entry
@Component
struct NavigationExample {
  @Provide('pageInfos') pageInfos: NavPathStack = new NavPathStack();
  private arr: number[] = [1, 2, 3];
  @State pageRootNode: FrameNode | null = null;

  @Builder
  pageMap(name: string) {
    if (name === 'NavDestinationTitle1') {
      PageOne();
    } else if (name === 'NavDestinationTitle2') {
      PageTwo();
    } else if (name === 'NavDestinationTitle3') {
      PageThree();
    }
  }

  onPageShow(): void {
    setTimeout(() => {
      this.pageRootNode = this.getUIContext()?.getPageRootNode();
      console.info('NavigationExample' + JSON.stringify(this.getUIContext().getPageRootNode()));
    });
  }

  build() {
    Column() {
      Navigation(this.pageInfos) {
        Text(`CurrentPageRootNode info: Tag ${this.pageRootNode?.getNodeType()}, NodeId： ${this.pageRootNode?.getUniqueId()}`)
          .width('90%')
          .height(40)
          .backgroundColor('#FFFFFF')
        List({ space: 12 }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('Page' + item)
                .width('100%')
                .height(72)
                .backgroundColor('#FFFFFF')
                .borderRadius(24)
                .fontSize(16)
                .fontWeight(500)
                .textAlign(TextAlign.Center)
                .onClick(() => {
                  this.pageInfos.pushPath({ name: 'NavDestinationTitle' + item });
                })
            }
          }, (item: number) => item.toString())
        }
        .width('100%')
        .margin({ top: 12 })
      }
      .title('主标题')
      .mode(NavigationMode.Stack)
      .navDestination(this.pageMap)
    }
    .height('100%')
    .width('100%')
    .backgroundColor('#F1F3F5')
  }
}

@Component
export struct PageOne {
  @Consume('pageInfos') pageInfos: NavPathStack;

  aboutToDisappear(): void {
    console.info('PageOne', 'aboutToDisappear');
  }

  build() {
    NavDestination() {
      Column() {
        Text('PageOne')
        Text(`CurrentPageRootNode info: Tag ${this.getUIContext()?.getPageRootNode()?.getNodeType()}, NodeId： ${this.getUIContext()?.getPageRootNode()?.getUniqueId()}`)
      }.width('100%').height('100%')
    }.title('NavDestinationTitle1')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // 弹出路由栈栈顶元素。
      console.info('pop' + '返回值' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

@Component
export struct PageTwo {
  @Consume('pageInfos') pageInfos: NavPathStack;

  build() {
    NavDestination() {
      Column() {
        Text('PageTwo')
        Text(`CurrentPageRootNode info: Tag ${this.getUIContext()?.getPageRootNode()?.getNodeType()}, NodeId： ${this.getUIContext()?.getPageRootNode()?.getUniqueId()}`)
      }.width('100%').height('100%')
    }.title('NavDestinationTitle2')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // 弹出路由栈栈顶元素。
      console.info('pop' + '返回值' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

@Component
export struct PageThree {
  @Consume('pageInfos') pageInfos: NavPathStack;

  build() {
    NavDestination() {
      Column() {
        Text('PageThree')
        Text(`CurrentPageRootNode info: Tag ${this.getUIContext()?.getPageRootNode()?.getNodeType()}, NodeId： ${this.getUIContext()?.getPageRootNode()?.getUniqueId()}`)
      }.width('100%').height('100%')
    }.title('NavDestinationTitle3')
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // 弹出路由栈栈顶元素。
      console.info('pop' + '返回值' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}
```

## getPixelRoundMode

```TypeScript
getPixelRoundMode(): PixelRoundMode
```

获取当前应用的像素取整模式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelRoundMode](arkts-arkui-pixelroundmode-e.md) | Pixel rounding mode of the current page. |

**示例**

```TypeScript
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {

      windowStage.loadContent('pages/Index', (err, data) => {
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        console.info("pixelRoundMode : " + uiContext.getPixelRoundMode().valueOf());
      });
    }
}
```

## getPromptAction

```TypeScript
getPromptAction(): PromptAction
```

get object PromptAction.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md) | PromptAction object. |

**示例**

完整示例请参考PromptAction中的示例。

## getRouter

```TypeScript
getRouter(): Router
```

Obtains a Router object.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Router](arkts-arkui-arkui-uicontext-router-c.md) | Router object. |

**示例**

完整示例请参考pushUrl。

## getSharedLocalStorage

```TypeScript
getSharedLocalStorage(): LocalStorage | undefined
```

获取当前stage共享的LocalStorage实例。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) \| undefined | LocalStorage** instance if it exists; **undefined** if it does not exist. |

**示例**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', this.storage);
  }
}
```

```TypeScript
// Index.ets

@Entry
@Component
struct SharedLocalStorage {
  localStorage = this.getUIContext().getSharedLocalStorage();

  build() {
    Row() {
      Column() {
        Button("Change Local Storage to 47")
          .onClick(() => {
            this.localStorage?.setOrCreate("propA", 47);
          })
        Button("Get Local Storage")
          .onClick(() => {
            console.info(`localStorage: ${this.localStorage?.get("propA")}`);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getSmartGestureController

```TypeScript
getSmartGestureController(): SmartGestureController
```

获取对象智能手势控制器。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SmartGestureController](arkts-arkui-arkui-uicontext-smartgesturecontroller-c.md) | 智能手势控制器对象。 |

**示例**

参考智慧手势控制器示例1（启用智慧手势并自定义动作处理）。

## getTextMenuController

```TypeScript
getTextMenuController(): TextMenuController
```

获取[TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md)对象，可通过该对象控制文本选择菜单。

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextMenuController](arkts-arkui-arkui-uicontext-textmenucontroller-c.md) | TextMenuController对象。 |

**示例**

参考TextMenuController接口示例。

## getUIInspector

```TypeScript
getUIInspector(): UIInspector
```

获取UIInspector对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIInspector](arkts-arkui-arkui-uicontext-uiinspector-c.md) | 返回UIInspector实例对象。 |

**示例**

完整示例请参考UIInspector中的示例。

## getUIObserver

```TypeScript
getUIObserver(): UIObserver
```

获取UIObserver对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIObserver](arkts-arkui-arkui-uicontext-uiobserver-c.md) | 返回UIObserver实例对象。 |

**示例**

```TypeScript
@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    this.getUIContext().getUIObserver().on('navDestinationUpdate', (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    this.getUIContext().getUIObserver().off('navDestinationUpdate');
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
        })
      }
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## getWindowHeightBreakpoint

```TypeScript
getWindowHeightBreakpoint(): HeightBreakpoint
```

获取当前实例所在窗口的高度断点。具体枚举值根据窗口高宽比确定，详见 [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md)。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md) | 当前实例所在窗口的高宽比对应的高度断点枚举值。若窗口高宽比为0，则返回HEIGHT_SM。 |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('test')
            .fontSize(30)
        }
        .onClick(() => {
          let uiContext: UIContext = this.getUIContext();
          let heightBp: HeightBreakpoint = uiContext.getWindowHeightBreakpoint();
          let widthBp: WidthBreakpoint = uiContext.getWindowWidthBreakpoint();
          console.info(`Window heightBP: ${heightBp}, widthBp: ${widthBp}`);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getWindowId

```TypeScript
getWindowId(): number | undefined
```

获取当前应用实例所属的窗口ID。

> **说明：**
> 
> 若UIContext位于主应用程序进程中的UIExtensionAbility内，则返回主应用程
> 序的顶层窗口ID。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number \| undefined | ID of the window to which the current application instance belongs. If the window does not exist, **undefined** is returned. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    const windowId = this.getUIContext().getWindowId();
    hilog.info(0x0000, 'testTag', 'current window id: %{public}d', windowId ?? -1);
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getWindowName

```TypeScript
getWindowName(): string | undefined
```

获取当前实例所在窗口的名称。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string \| undefined | Name of the window where the current instance is located. If the window does not exist, **undefined** is returned. |

**示例**

```TypeScript
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    const windowName = this.getUIContext().getWindowName();
    console.info('WindowName ' + windowName);
    if (windowName) {
      const currWindow = window.findWindow(windowName);
      const windowProperties = currWindow.getWindowProperties();
      console.info(`Window width ${windowProperties.windowRect.width}, height ${windowProperties.windowRect.height}`);
    }
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## getWindowWidthBreakpoint

```TypeScript
getWindowWidthBreakpoint(): WidthBreakpoint
```

获取当前实例所在窗口的宽度断点枚举值。具体枚举值根据窗口宽度vp值确定，详见 [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md)。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md) | 当前实例所在窗口的宽度断点枚举值。若窗口宽度为 0vp，则返回WIDTH_XS。 |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('test')
            .fontSize(30)
        }
        .onClick(() => {
          let uiContext: UIContext = this.getUIContext();
          let widthBp: WidthBreakpoint = uiContext.getWindowWidthBreakpoint();
          console.info(`Window widthBp: ${widthBp}`);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## isAvailable

```TypeScript
isAvailable(): boolean
```

判断UIContext对象对应的UI实例是否有效。使用 getUIContext方法获取UIContext对象。后端UI实例存在时， 该UI实例有效。通过new UIContext()创建的UIContext对象无对应的UI实例；多次 [loadContent](arkts-arkui-window-window-i.md#loadcontent)后，旧的UI实例会失效。多窗口应用场景，当窗口关闭后，该窗 口的UI实例失效。总而言之，当UIContext对象没有对应的后端UI实例时，该对象是无效的。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回UIContext对象对应的UI实例是否有效。true表示有效，false表示无效。 |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct UIContextCompare {
  @State result1: string = '';
  @State result2: string = '';

  build() {
    Column() {
      Text('getUIContext() 结果: ' + this.result1)
        .fontSize(20)
        .margin(10)

      Text('new UIContext() 结果: ' + this.result2)
        .fontSize(20)
        .margin(10)

      Divider().margin(20)

      Button('getUIContext()')
        .width('70%')
        .height(50)
        .margin(10)
        .onClick(() => {
          try {
            const ctx: UIContext = this.getUIContext();
            const available: boolean = ctx.isAvailable();
            this.result1 = `可用状态: ${available} UI实例有效 `;
            console.info('getUIContext测试:', available);
          } catch (error) {
            this.result1 = '错误: ' + (error instanceof Error ? error.message : String(error));
          }
        })

      Button('new UIContext()')
        .width('70%')
        .height(50)
        .margin(10)
        .onClick(() => {
          try {
            const ctx: UIContext = new UIContext();
            const available: boolean = ctx.isAvailable();
            this.result2 = `可用状态: ${available} UI实例无效`;
            console.info('new UIContext测试:', available);
          } catch (error) {
            this.result2 = '错误: ' + (error instanceof Error ? error.message : String(error));
          }
        })
    }
    .width('100%')
    .height('100%')
    .padding(20)
  }
}
```

## isEasySplit

```TypeScript
isEasySplit(): boolean
```

检查当前UI实例是否处于分栏模式。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前UI实例是否处于分栏模式。true表示处于分栏模式，false表示未处于分栏模式。 |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  @State isEasySplit: boolean = false;

  build() {
    Column() {
      Text(`${this.isEasySplit ? 'current is easy split mode' : 'current is not easy split mode'}`)
        .fontSize(20)
        .margin(10)
      Button('Check EasySplit')
        .onClick(() => {
          this.isEasySplit = this.getUIContext()?.isEasySplit();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## isFollowingSystemFontScale

```TypeScript
isFollowingSystemFontScale(): boolean
```

Checks whether current font scale follows the system.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if current font scale follows the system; returns false otherwise. |

**示例**

参考[configuration标签](../../../quick-start/app-configuration-file.md#configuration标签)，配置fontSizeScale的值为“followSystem”。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('isFollowingSystemFontScale').onClick(() => {
        console.info('isFollowingSystemFontScale', this.getUIContext().isFollowingSystemFontScale());
      });
    }
  }
}
```

## keyframeAnimateTo

```TypeScript
keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array<KeyframeState>): void
```

产生关键帧动画。该接口的使用说明请参考keyframeAnimateTo。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [KeyframeAnimateParam](../arkts-components/arkts-arkui-keyframeanimateparam-i.md) | 是 | 关键帧动画的整体动画参数。 |
| keyframes | Array&lt;[KeyframeState](../arkts-components/arkts-arkui-keyframestate-i.md)&gt; | 是 | 所有的关键帧状态的列表。 |

**示例**

```TypeScript
// xxx.ets
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct KeyframeDemo {
  @State myScale: number = 1.0;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext();
  }

  build() {
    Column() {
      Circle()
        .width(100)
        .height(100)
        .fill("#46B1E3")
        .margin(100)
        .scale({ x: this.myScale, y: this.myScale })
        .onClick(() => {
          if (!this.uiContext) {
            console.error("no uiContext, keyframe failed");
            return;
          }
          this.myScale = 1;
          // 设置关键帧动画整体播放3次
          this.uiContext.keyframeAnimateTo({
              iterations: 3,
              expectedFrameRateRange: {
                min: 10,
                max: 120,
                expected: 60,
              }
            }, [
            {
              // 第一段关键帧动画时长为800ms，scale属性做从1到1.5的动画
              duration: 800,
              event: () => {
                this.myScale = 1.5;
              }
            },
            {
              // 第二段关键帧动画时长为500ms，scale属性做从1.5到1的动画
              duration: 500,
              event: () => {
                this.myScale = 1;
              }
            }
          ]);
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## lpx2px

```TypeScript
lpx2px(value: number): number
```

将lpx单位的数值转换为以px为单位的数值。转换公式为：px值 = lpx值 × 实际屏幕宽度与逻辑宽度（通过[designWidth](../../../quick-start/module-configuration-file.md#pages标签)配置）的比值。

> **说明：**
> 
> getUIContext需在windowStage.
> [loadContent](arkts-arkui-window-window-i.md#loadcontent)之后调用，确保UIContext初始化完成后
> 调用此接口，否则无法返回准确结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的数值。 |

**示例**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().lpx2px(50),
          centerY: this.getUIContext().lpx2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## openBindSheet

```TypeScript
openBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions?: SheetOptions, targetId?: number): Promise<void>
```

创建并弹出以bindSheetContent作为内容的半模态页面，使用Promise异步回调。通过该接口弹出的半模态页面样式完全按照bindSheetContent中设置的样式显示。

> **说明：**
> 
> 1. 使用该接口时，若未传入有效的targetId，则不支持设置SheetOptions.preferType为POPUP模式、不支持设置SheetOptions.mode为EMBEDDED模式。
> 
> 2. 由于[updateBindSheet](#updatebindsheet)和[closeBindSheet](#closebindsheet)依赖
> bindSheetContent去更新或者关闭指定的半模态页面，开发者需自行维护传入的bindSheetContent。
> 
> 3. 不支持设置SheetOptions.UIContext。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | 是 | 半模态页面中显示的组件内容。 |
| sheetOptions | [SheetOptions](../arkts-components/arkts-arkui-sheetoptions-i.md) | 否 | 半模态页面样式。   **说明：** 1. 不支持设置SheetOptions.uiContext，该属性的值固定为当前实例的 UIContext。 2. 若不传递targetId，则不支持设置SheetOptions.preferType为POPUP样式，若设置了POPUP样式则使用CENTER样式替代。 3. 若不传递 targetId，则不支持设置SheetOptions.mode为EMBEDDED模式，默认为OVERLAY模式。 4. 其余属性的默认值参考[SheetOptions](../arkts-components/arkts-arkui-sheetoptions-i.md)文 档。 |
| targetId | number | 否 | 需要绑定组件的ID，若不指定则不绑定任何组件。id不存在时返回错误码120004。在传入undefined时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-内容节点对应半模态页面错误) | The bindSheetContent is incorrect. |
| [120002](../errorcode-bindSheet.md#120002-内容节点对应半模态页面已存在) | The bindSheetContent already exists. |
| [120004](../errorcode-bindSheet.md#120004-指定的targetid不存在) | The targetId does not exist. |
| [120005](../errorcode-bindSheet.md#120005-指定的targetid对应的节点未挂载在组件树上) | The node of targetId is not in the component tree. |
| [120006](../errorcode-bindSheet.md#120006-指定的targetid对应的节点并不是page节点或navdestination节点的子节点) | The node of targetId is not a child of the page node or NavDestination node. |

**示例**

```TypeScript
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.error('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## postDelayedFrameCallback

```TypeScript
postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void
```

注册一个回调，在延迟一段时间后的下一帧进行渲染时执行。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameCallback | [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | 是 | 下一帧需要执行的回调。 |
| delayTime | number | 是 | 延迟的时间，以毫秒为单位。传入null、undefined或小于0的值，会按0处理。 |

**示例**

```TypeScript
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button('点击触发postDelayedFrameCallback')
        .onClick(() => {
          this.getUIContext().postDelayedFrameCallback(new MyFrameCallback('delayTask'), 5);
        })
    }
  }
}
```

## postFrameCallback

```TypeScript
postFrameCallback(frameCallback: FrameCallback): void
```

注册一个回调，仅在下一帧渲染时调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameCallback | [FrameCallback](arkts-arkui-arkui-uicontext-framecallback-c.md) | 是 | 下一帧需要执行的回调。 |

**示例**

```TypeScript
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button('点击触发postFrameCallback')
        .onClick(() => {
          this.getUIContext().postFrameCallback(new MyFrameCallback('normTask'));
        })
    }
  }
}
```

## px2fp

```TypeScript
px2fp(value: number): number
```

将px单位的数值转换为以fp为单位的数值。转换公式为：fp值 = px值 ÷ 像素密度 ÷ 字体缩放比例像素密度：当前窗口生效的像素密度值，即虚拟屏幕的密度[VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md).density。字体缩放比例：系统设置的字体缩放系数，对应 Configuration.fontScale。

> **说明：**
> 
> getUIContext需在windowStage.
> [loadContent](arkts-arkui-window-window-i.md#loadcontent)之后调用，确保UIContext初始化完成后
> 调用此接口，否则无法返回准确结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的数值。 |

**示例**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2fp(50),
          centerY: this.getUIContext().px2fp(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## px2lpx

```TypeScript
px2lpx(value: number): number
```

将px单位的数值转换为以lpx为单位的数值。转换公式为：lpx值 = px值 ÷ 实际屏幕宽度与逻辑宽度（通过[designWidth](../../../quick-start/module-configuration-file.md#pages标签)配置）的比值。

> **说明：**
> 
> getUIContext需在windowStage.
> [loadContent](arkts-arkui-window-window-i.md#loadcontent)之后调用，确保UIContext初始化完成后
> 调用此接口，否则无法返回准确结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的数值。 |

**示例**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2lpx(50),
          centerY: this.getUIContext().px2lpx(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## px2vp

```TypeScript
px2vp(value: number): number
```

将px单位的数值转换为以vp为单位的数值。转换公式为：vp值 = px值 ÷ 像素密度像素密度：当前窗口生效的像素密度值，即虚拟屏幕的密度[VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md).density。

> **说明：**
> 
> 1. getUIContext需在windowStage.
> [loadContent](arkts-arkui-window-window-i.md#loadcontent)之后调用，确保UIContext初始化完成后
> 调用此接口，否则无法返回准确结果。
> 
> 2. UI实例未创建时，像素单位中的px2vp接口使用默认屏幕的虚拟像素比进行转换。在该场景下，开发者使用UIContext接口替换时，可参考
> [像素单位转换接口替换为UIContext接口](../../../ui/arkts-global-interface.md#像素单位转换接口替换为uicontext接口)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的数值。 |

**示例**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2vp(50),
          centerY: this.getUIContext().px2vp(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

## removeLocalInputEventMonitor

```TypeScript
removeLocalInputEventMonitor(monitor: InputEventMonitor): void
```

删除本地输入事件监视器。  
**重要说明**： -只能移除addLocalInputEventMonitor返回的Monitor对象。 -无法通过手动构造对象来注销监视器。 -如果传递了一个无效的对象，系统会默默地忽略它。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitor | [InputEventMonitor](../arkts-components/arkts-arkui-inputeventmonitor-i.md) | 是 | 监控标识对象（由addLocalInputEventMonitor返回）。 |

**示例**

```TypeScript
@Entry
@Component
struct RemoveMonitorSample {
  private uiContext: UIContext | undefined = undefined;
  private monitor: InputEventMonitor | null = null;
  aboutToAppear() {
    this.uiContext = this.getUIContext();
    this.monitor = this.uiContext.addLocalInputEventMonitor(
      InputEventSubTypeMask.LEFT_MOUSE_DOWN,
      (wrapper: RawInputEventWrapper) => {
        return { action: InputEventInterceptAction.CONTINUE };
      }
    );
  }
  aboutToDisappear() {
    // 组件销毁时移除监听器
    if (this.monitor && this.uiContext) {
      this.uiContext.removeLocalInputEventMonitor(this.monitor);
    }
  }
  build() {
    Column() {
      Button('Remove Monitor')
        .onClick(() => {
          if (this.monitor && this.uiContext) {
            this.uiContext.removeLocalInputEventMonitor(this.monitor);
            this.monitor = null;
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## requireDynamicSyncScene

```TypeScript
requireDynamicSyncScene(id: string): Array<DynamicSyncScene>
```

请求组件的动态帧率场景，用于自定义场景相关帧率配置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 节点对应的组件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[DynamicSyncScene](arkts-arkui-arkui-uicontext-dynamicsyncscene-c.md)&gt; | The instance of SwiperDynamicSyncScene. |

**示例**

```TypeScript
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State animationFrameRateRange: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State gestureFrameRateRange: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("动画" + JSON.stringify(this.animationFrameRateRange))
      Text("跟手" + JSON.stringify(this.gestureFrameRateRange))
      Row() {
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(() => {
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scenes: SwiperDynamicSyncScene) => {

            if (scenes.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.animationFrameRateRange);
            }

            if (scenes.type == SwiperDynamicSyncSceneType.GESTURE) {
              scenes.setFrameRateRange(this.gestureFrameRateRange);
            }
          });
        })
    }
  }
}
```

## resolveUIContext

```TypeScript
static resolveUIContext(): ResolvedUIContext
```

使用优先级策略获取带有解析策略的UIContext实例对象。

> **说明：**
> 
> 按照预定义的优先级顺序解析并返回UIContext实例和UIContext的解析策略。
> 
> 解析规则按顺序如下：
> 
> 1. 当前调用作用域中的UIContext。
> 
> 2. 如果只存在一个UI实例，则返回其UIContext。
> 
> 3. 如果存在UI实例切换到获焦状态，且最近一次切换到获焦状态的UI实例未销毁，则返回最近一次获焦UI实例的UIContext。
> 
> 4. 如果存在UI实例切换到前台状态，且最近一次切换到前台状态的UI实例未销毁，则返回最近一次切换到前台状态的UI实例的UIContext。
> 
> 5. 如果存在多个UI实例，则返回实例唯一标识的ID最大的UIContext。
> 
> 6. 如果以上条件均不满足，则返回一个无效的UIContext实例。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ResolvedUIContext](arkts-arkui-arkui-uicontext-resolveduicontext-c.md) | 返回带有解析策略的UIContext实例对象。 |

**示例**

```TypeScript
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('click').onClick(() => {
        let resolvedUIContext = UIContext.resolveUIContext();
        hilog.info(0x00, 'testTag', `UIContext id: ${resolvedUIContext.getId()}, strategy: ${resolvedUIContext.strategy}`);
      })
    }
    .width(UIContext.resolveUIContext().px2vp(100))
    .height('100%')
  }
}
```

## runScopedTask

```TypeScript
runScopedTask(callback: () => void): void
```

在当前UIContext对应的UI实例作用域内执行传入的回调函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 需要在当前UIContext对应的UI实例作用域内执行的回调函数。 |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  private selectedDate: Date = new Date('2025-10-01');

  build() {
    Button('Show CalendarPicker Dialog')
      .onClick(() => {
        const uiContext = this.getUIContext();
        uiContext.runScopedTask(() => {
          CalendarPickerDialog.show({
            selected: this.selectedDate
          });
        });
      });
  }
}
```

## setCustomKeyboardContinueFeature

```TypeScript
setCustomKeyboardContinueFeature(feature: CustomKeyboardContinueFeature): void
```

设置自定义键盘接续特性。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| feature | [CustomKeyboardContinueFeature](arkts-arkui-arkui-uicontext-customkeyboardcontinuefeature-e.md) | 是 | 自定义键盘接续特性。 |

**示例**

```TypeScript
// xxx.ets
import { CustomKeyboardContinueFeature } from '@ohos.arkui.UIContext';

@Entry
@Component
struct Index {
  controller: TextInputController = new TextInputController();
  controller2: TextInputController = new TextInputController();
  @State inputValue: string = '';
  @State inputValue2: string = '';
  @State supportAvoidance: boolean = true;
  @State isValue: CustomKeyboardContinueFeature = CustomKeyboardContinueFeature.DISABLED;
  @State str: string = '否';

  // 自定义键盘组件
  @Builder
  CustomKeyboardBuilder() {
    Column() {
      Row() {
        Button('x').onClick(() => {
          // 关闭自定义键盘
          this.controller.stopEditing();
        }).margin(10)
        Button('delete').onClick(() => {
          this.inputValue = this.inputValue.slice(0, -1);
        }).margin(10)
      }

      Grid() {
        ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, '*', 0, '#'], (item: number | string) => {
          GridItem() {
            Button(item + '')
              .width(110).onClick(() => {
              this.inputValue += item;
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }.backgroundColor('rgb(213, 213, 213)').height(300)
  }

  // 自定义键盘组件
  @Builder
  CustomKeyboardBuilder2() {
    Column() {
      Row() {
        Button('x').onClick(() => {
          // 关闭自定义键盘
          this.controller2.stopEditing();
        }).margin(10)
        Button('delete').onClick(() => {
          this.inputValue2 = this.inputValue2.slice(0, -1);
        }).margin(10)
      }

      Grid() {
        ForEach([1, 2, 3, 4, 5, 6, 7, 8, 9, '*', 0, '#'], (item: number | string) => {
          GridItem() {
            Button(item + '')
              .width(110).onClick(() => {
              this.inputValue2 += item;
            })
          }
        })
      }.maxCount(3).columnsGap(10).rowsGap(10).padding(5)
    }.backgroundColor('rgb(227, 248, 249)').height(150)
  }

  build() {
    Scroll() {
      Column() {
        Button('是否接续：' + this.str).onClick(() => {
          if (this.isValue == CustomKeyboardContinueFeature.ENABLED) {
            this.isValue = CustomKeyboardContinueFeature.DISABLED
            this.str = '否'
          } else {
            this.isValue = CustomKeyboardContinueFeature.ENABLED
            this.str = '是'
          }
          this.getUIContext().setCustomKeyboardContinueFeature(this.isValue);
        }).fontSize(20).width('80%').key('button')

        TextInput({
          placeholder: 'TextInput1 bind CustomKeyboardBuilder',
          controller: this.controller,
          text: this.inputValue
        })// 绑定自定义键盘
          .customKeyboard(this.CustomKeyboardBuilder(), { supportAvoidance: this.supportAvoidance })
          .margin(10)
          .border({ width: 1 })
        TextInput({
          placeholder: 'TextInput2 bind CustomKeyboardBuilder2',
          controller: this.controller2,
          text: this.inputValue2
        })// 绑定自定义键盘
          .customKeyboard(this.CustomKeyboardBuilder2(), { supportAvoidance: this.supportAvoidance })
          .margin(10)
          .border({ width: 1 })
      }
    }
  }
}
```

## setImageCacheCount

```TypeScript
setImageCacheCount(value: number): void
```

设置内存中缓存解码后图片的数量上限，提升再次加载同源图片的加载速度。如果不设置则默认为0，不进行缓存。缓存采用内置的LRU策略，新图片加载后，如果超过缓存上限，会删除最久未再次加载的缓存。 建议根据应用内存需求，设置合理缓存数量，数字过大可能导致内存使用过高。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 内存中缓存解码后图片的数量上限 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  onPageShow() {
    // 设置解码后图片内存缓存上限为100张
    this.getUIContext().setImageCacheCount(100);
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      Image('https://www.example.com/xxx.png') // 请填写一个具体的网络图片地址
        .width(200)
        .height(50)
    }.width('100%')
  }
}
```

## setImageRawDataCacheSize

```TypeScript
setImageRawDataCacheSize(value: number): void
```

设置内存中缓存解码前图片数据的大小上限，单位为字节，提升再次加载同源图片的加载速度。如果不设置则默认为0，不进行缓存。缓存采用内置的LRU策略，新图片加载后，如果解码前数据超过缓存上限，会删除最久未再次加载的图片数据缓存。 建议根据应用内存需求，设置合理缓存上限，过大可能导致应用内存使用过高。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | capacity of raw image data size in bytes. |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  onPageShow() {
    // 设置解码前图片数据内存缓存上限为100MB (100MB=100*1024*1024B=104857600B)
    this.getUIContext().setImageRawDataCacheSize(104857600); 
    console.info('Application onPageShow');
  }
  onDestroy() {
    console.info('Application onDestroy');
  }

  build() {
    Row(){
      Image('https://www.example.com/xxx.png') // 请填写一个具体的网络图片地址
        .width(200)
        .height(50)
    }.width('100%')
  }
}
```

## setKeyboardAvoidMode

```TypeScript
setKeyboardAvoidMode(value: KeyboardAvoidMode): void
```

控制虚拟键盘抬起时页面的避让模式。

> **说明：**
> 
> KeyboardAvoidMode.RESIZE模式会压缩页面大小，页面中设置百分比宽高的组件会跟随页面压缩，而直接设置宽高的组件会按设置的固定大小布局。设置KeyboardAvoidMode的RESIZE模式时，expandSa feArea([SafeAreaType.KEYBOARD],[SafeAreaEdge.BOTTOM])不生效。
> 
> KeyboardAvoidMode.NONE模式配置页面不避让键盘，页面会被抬起的键盘遮盖。
> 
> setKeyboardAvoidMode针对页面生效，对于弹窗类组件不生效，比如Dialog、Popup、Menu、BindSheet、BindContentCover、Toast、OverlayManager。弹窗类组件的避让模 式可以参考CustomDialogControllerOptions对象说明。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [KeyboardAvoidMode](arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) | 是 | 配置虚拟键盘抬起时页面的避让模式。默认值：KeyboardAvoidMode.OFFSET，键盘抬起时默认避让模式为上抬。setKeyboardAvoidMode传入异常值时，该属性设置不生效。 |

**示例**

完整示例请参考示例4（设置键盘避让模式为压缩）、示例5（设置键盘避让模式为上抬）以及示例6（切换避让模式）。

```TypeScript
// EntryAbility.ets
import { KeyboardAvoidMode, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility{
  onWindowStageCreate(windowStage: window.WindowStage) {

      windowStage.loadContent('pages/Index', (err, data) => {
        let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
        uiContext.setKeyboardAvoidMode(KeyboardAvoidMode.RESIZE);
      });
    }
}
```

## setOverlayManagerOptions

```TypeScript
setOverlayManagerOptions(options: OverlayManagerOptions): boolean
```

Init OverlayManager.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OverlayManagerOptions](arkts-arkui-arkui-uicontext-overlaymanageroptions-i.md) | 是 | Options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if it is called first and before getting an OverlayManager instance; returns false otherwise. |

**示例**

完整示例请参考OverlayManager中的示例。

## setPixelRoundMode

```TypeScript
setPixelRoundMode(mode: PixelRoundMode): void
```

设置当前页面的像素取整模式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [PixelRoundMode](arkts-arkui-pixelroundmode-e.md) | 是 | 像素取整模式。默认值：PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH设置异常值时，该属性为默认值。 |

**示例**

```TypeScript
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {

    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      uiContext.setPixelRoundMode(PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH);
    });
  }
}
```

## setResourceManagerCacheMaxCountForHSP

```TypeScript
static setResourceManagerCacheMaxCountForHSP(count: number): void
```

设置HSP资源管理对象的缓存数量上限。如果缓存的上限设置得过高，可能会导致内存开销过大，存在内存过载的风险。 建议根据实际需求进行配置。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | HSP资源管理器的缓存限制必须为非负整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100101](../errorcode-uicontext.md#100101-小于0的非法值) | The parameter is less than 0. |
| [100102](../errorcode-uicontext.md#100102-参数类型错误) | The parameter value cannot be a floating point number. |
| [100103](../errorcode-uicontext.md#100103-调用线程错误) | The function cannot be called from a non main thread. |

**示例**

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext, window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', err.message);
        return;
      }
      UIContext.setResourceManagerCacheMaxCountForHSP(5);
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

## setTextSelectionClearPolicy

```TypeScript
setTextSelectionClearPolicy(policy: TextSelectionClearPolicy): void
```

设置文本组件的文本选择清除策略。 默认策略：**TextSelectionClearPolicy.KEEP_ON_EXTERNAL_CLICK**。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [TextSelectionClearPolicy](arkts-arkui-arkui-uicontext-textselectionclearpolicy-e.md) | 是 | 文本选择清除策略。 |

**示例**

```TypeScript
import { TextSelectionClearPolicy } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .margin(10)
        .copyOption(CopyOptions.LocalDevice)
      Button('Set Clear Policy')
        .onClick(() => {
          this.getUIContext()?.setTextSelectionClearPolicy(TextSelectionClearPolicy.CLEAR_SELECTED_TEXT_ON_EXTERNAL_TOUCH);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## showActionSheet

```TypeScript
showActionSheet(value: ActionSheetOptions): void
```

Shows an action sheet in the given settings.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | 是 | Parameters of the action sheet. |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  uiContext: UIContext = this.getUIContext()

  build() {
    Column() {
      Button('showActionSheet')
        .onClick(() => {
          this.uiContext.showActionSheet({
            title: 'ActionSheet title',
            message: 'message',
            autoCancel: true,
            confirm: {
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          });
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## showAlertDialog

```TypeScript
showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): void
```

alertDialog display.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) \| [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) \| [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | 是 | Shows an AlertDialog component in the given settings. |

**示例**

```TypeScript
@Entry
@Component
struct Index {
  uiContext: UIContext = this.getUIContext()

  build() {
    Column() {
      Button('showAlertDialog')
        .onClick(() => {
          this.uiContext.showAlertDialog(
            {
              title: 'title',
              message: 'text',
              autoCancel: true,
              alignment: DialogAlignment.Bottom,
              offset: { dx: 0, dy: -20 },
              gridCount: 3,
              confirm: {
                value: 'button',
                action: () => {
                  console.info('Button-clicking callback');
                }
              },
              cancel: () => {
                console.info('Closed callbacks');
              }
            }
          );
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

## showDatePickerDialog

```TypeScript
showDatePickerDialog(options: DatePickerDialogOptions): void
```

datePickerDialog display.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](../arkts-components/arkts-arkui-datepickerdialogoptions-i.md) | 是 | Options. |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Row(){
      Column() {
        Button("DatePickerDialog")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showDatePickerDialog({
              start: new Date("2000-1-1"),
              end: new Date("2100-12-31"),
              selected: this.selectedDate,
              showTime: true,
              useMilitaryTime: false,
              dateTimeOptions: { hour: "numeric", minute: "2-digit" },
              onDateAccept: (value: Date) => {
                // 通过Date的setFullYear方法设置按下确定按钮时的日期，这样当弹窗再次弹出时显示选中的是上一次确定的日期
                this.selectedDate = value;
                console.info("DatePickerDialog:onDateAccept()" + value.toString());
              },
              onCancel: () => {
                console.info("DatePickerDialog:onCancel()");
              },
              onDateChange: (value: Date) => {
                console.info("DatePickerDialog:onDateChange()" + value.toString());
              },
              onDidAppear: () => {
                console.info("DatePickerDialog:onDidAppear()");
              },
              onDidDisappear: () => {
                console.info("DatePickerDialog:onDidDisappear()");
              },
              onWillAppear: () => {
                console.info("DatePickerDialog:onWillAppear()");
              },
              onWillDisappear: () => {
                console.info("DatePickerDialog:onWillDisappear()");
              }
            })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

## showTextPickerDialog

```TypeScript
showTextPickerDialog(options: TextPickerDialogOptions): void
```

textPickerDialog display.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](../arkts-components/arkts-arkui-textpickerdialogoptions-i.md) | 是 | Options. |

**示例**

```TypeScript
// xxx.ets

class SelectedValue{
  select: number = 2;
  set(val: number){
    this.select = val;
  }
}
class SelectedArray{
  select: number[] = [];
  set(val: number[]){
    this.select = val;
  }
}
@Entry
@Component
struct TextPickerDialogExample {
  @State selectTime: Date = new Date('2023-12-25T08:30:00');
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4', 'banana5'];
  private select: number  = 0;
  build() {
    Row(){
      Column() {
        Button('showTextPickerDialog')
          .margin(30)
          .onClick(() => {
            this.getUIContext().showTextPickerDialog({
              range: this.fruits,
              selected: this.select,
              onAccept: (value: TextPickerResult) => {
                // 设置select为按下确定按钮时候的选中项index，这样当弹窗再次弹出时显示选中的是上一次确定的选项
                let selectedVal = new SelectedValue();
                let selectedArr = new SelectedArray();
                if (value.index){
                  value.index instanceof Array?selectedArr.set(value.index) : selectedVal.set(value.index);
                }
                console.info("TextPickerDialog:onAccept()" + JSON.stringify(value));
              },
              onCancel: () => {
                console.info("TextPickerDialog:onCancel()");
              },
              onChange: (value: TextPickerResult) => {
                console.info("TextPickerDialog:onChange()" + JSON.stringify(value));
              }
            });
          })
      }.width('100%').margin({ top: 5 })
    }.height('100%')
  }
}
```

## showTextPickerDialog

```TypeScript
showTextPickerDialog(style: TextPickerDialogOptions | TextPickerDialogOptionsExt): void
```

textPickerDialog display.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextPickerDialogOptions](../arkts-components/arkts-arkui-textpickerdialogoptions-i.md) \| [TextPickerDialogOptionsExt](../arkts-components/arkts-arkui-textpickerdialogoptionsext-i.md) | 是 | Dialog style. |

**示例**

参见 [showTextPickerDialog](#showtextpickerdialog)

## showTimePickerDialog

```TypeScript
showTimePickerDialog(options: TimePickerDialogOptions): void
```

timePickerDialog display.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](../arkts-components/arkts-arkui-timepickerdialogoptions-i.md) | 是 | Options. |

**示例**

```TypeScript
// xxx.ets

class SelectTime{
  selectTime: Date = new Date('2020-12-25T08:30:00');
  hours(h:number,m:number){
    this.selectTime.setHours(h, m);
  }
}

@Entry
@Component
struct TimePickerDialogExample {
  @State selectTime: Date = new Date('2023-12-25T08:30:00');

  build() {
    Column() {
      Button('showTimePickerDialog')
        .margin(30)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            selected: this.selectTime,
            onAccept: (value: TimePickerResult) => {
              // 设置selectTime为按下确定按钮时的时间，这样当弹窗再次弹出时显示选中的为上一次确定的时间
              let time = new SelectTime();
              if(value.hour && value.minute){
                time.hours(value.hour, value.minute);
              }
              console.info("TimePickerDialog:onAccept()" + JSON.stringify(value));
            },
            onCancel: () => {
              console.info("TimePickerDialog:onCancel()");
            },
            onChange: (value: TimePickerResult) => {
              console.info("TimePickerDialog:onChange()" + JSON.stringify(value));
            }
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

## unbindTabsFromNestedScrollable

```TypeScript
unbindTabsFromNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void
```

Unbind tabs from nested scrollable container components.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | 是 | The controller of the tabs. |
| parentScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | 是 | The controller of the parent scrollable container component. |
| childScroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | 是 | The controller of the child scrollable container component. |

**示例**

参考[bindTabsToScrollable](#bindtabstoscrollable)接口示例。

## unbindTabsFromScrollable

```TypeScript
unbindTabsFromScrollable(tabsController: TabsController, scroller: Scroller): void
```

Unbind tabs from scrollable container component.

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabsController | [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md) | 是 | The controller of the tabs. |
| scroller | [Scroller](../arkts-components/arkts-arkui-scroller-c.md) | 是 | The controller of the scrollable container component. |

**示例**

参考[bindTabsToScrollable](#bindtabstoscrollable)接口示例。

## updateBindSheet

```TypeScript
updateBindSheet<T extends Object>(bindSheetContent: ComponentContent<T>, sheetOptions: SheetOptions, partialUpdate?: boolean): Promise<void>
```

更新bindSheetContent对应的半模态页面的样式，使用Promise异步回调。

> **说明：**
> 
> 不支持更新SheetOptions.UIContext、SheetOptions.mode、回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bindSheetContent | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; | 是 | 半模态页面中显示的组件内容。 |
| sheetOptions | [SheetOptions](../arkts-components/arkts-arkui-sheetoptions-i.md) | 是 | 半模态页面样式。   **说明：** 不支持更新SheetOptions.uiContext、SheetOptions.mode、回调函 数。 |
| partialUpdate | boolean | 否 | 半模态页面更新方式, 默认值为false。   **说明：** 1. true为增量更新，保留当前值，更新SheetOptions中的指定属性。  2. false为全量更新，除SheetOptions中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [120001](../errorcode-bindSheet.md#120001-内容节点对应半模态页面错误) | The bindSheetContent is incorrect. |
| [120003](../errorcode-bindSheet.md#120003-无法找到内容节点对应的半模态页面) | The bindSheetContent cannot be found. |

**示例**

```TypeScript
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.error('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.error('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

## vp2px

```TypeScript
vp2px(value: number): number
```

将vp单位的数值转换为以px为单位的数值。转换公式为：px值 = vp值 × 像素密度像素密度：当前窗口生效的像素密度值，即虚拟屏幕的密度[VirtualScreenConfig](arkts-arkui-display-virtualscreenconfig-i.md).density。

> **说明：**
> 
> 1. getUIContext需在windowStage.
> [loadContent](arkts-arkui-window-window-i.md#loadcontent)之后调用，确保UIContext初始化完成后
> 调用此接口，否则无法返回准确结果。
> 
> 2. UI实例未创建时，像素单位中的vp2px接口使用默认屏幕的虚拟像素比进行转换。在该场景下，开发者使用UIContext接口替换时，可参考
> [像素单位转换接口替换为UIContext接口](../../../ui/arkts-global-interface.md#像素单位转换接口替换为uicontext接口)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 转换后的数值。 |

**示例**

```TypeScript
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().vp2px(50),
          centerY: this.getUIContext().vp2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```
