# UIObserver

```TypeScript
export class UIObserver
```

UIObserver提供了UI组件行为变化的无感监听能力，支持监听Navigation页面状态变化（NavDestination）、滚动事件、路由页面状态、屏幕像素密度变化、绘制指令下发、布局完成、页面切换等多种UI组件行为。开发者可以通过该模块实现对UI组件状态的实时感知和追踪，适用于需要监控页面生命周期、处理滚动事件、优化渲染性能等场景，帮助开发者更好地理解和管理UI组件的行为变化。无感监听是指在组件状态变化时，系统自动触发回调函数通知开发者，无需开发者手动轮询或主动查询组件状态。监听器通过注册回调函数实现，当目标组件状态改变时，系统内部的事件分发机制会调用已注册的回调函数，携带状态变化信息。

> **说明：** 

> - 以下API需先使用UIContext中的[getUIObserver()](arkts-arkui-arkui-uicontext-uicontext-c.md#getuiobserver)方法获取到UIObserver对象，再通过该对象调用对应方法。
> 
> - UIObserver仅能监听到本进程内的UI组件状态变化信息，不支持获取<!--Del-->UIExtensionComponent等<!--DelEnd-->跨进程场景的信息。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## addGlobalGestureListener

```TypeScript
addGlobalGestureListener(type: GestureListenerType,
      option: GestureObserverConfigs, callback: GestureListenerCallback): void
```

注册回调函数以监听手势触发信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | 是 | 要监听的手势类型。 |
| option | [GestureObserverConfigs](arkts-arkui-arkui-uicontext-gestureobserverconfigs-i.md) | 是 | 绑定全局监听器时的配置选项。 |
| callback | [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 是 | 手势状态更新时的回调函数。 |

**示例**

该示例使用全局手势监听器实时追踪Tap、Pan和LongPress三个独立区域的触发状态，记录各手势的触发次数和最后操作信息，并在组件生命周期内自动管理监听器的注册与注销。

```TypeScript
// Index.ets
// 演示uiObserver.addGlobalGestureListener(type, option, callback)
// uiObserver.removeGlobalGestureListener(type, callback)

import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureListenerCallback } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tapCount: number = 0;
  @State panCount: number = 0;
  @State longPressCount: number = 0;
  @State lastAction: string = '无';
  @State lastArea: string = '无';

  // 存储监听器回调引用
  private tapCallback?: GestureListenerCallback;
  private panCallback?: GestureListenerCallback;
  private longPressCallback?: GestureListenerCallback;

  // 启用全局监听
  aboutToAppear() {
    this.addGlobalListeners();
  }
  // 终止全局监听
  aboutToDisappear() {
    this.removeGlobalListeners();
  }

  private addGlobalListeners() {
    const observer = this.getUIContext().getUIObserver();

    // Tap监听任务
    this.tapCallback = (info: GestureTriggerInfo) => {
      if (info.event?.target?.id === 'tap-area') {
        this.tapCount++;
        this.lastAction = '点击';
        this.lastArea = 'Tap区域';
      }
    };
    observer.addGlobalGestureListener(
      GestureListenerType.TAP,
      { actionPhases: [GestureActionPhase.WILL_START, GestureActionPhase.WILL_END] },
      this.tapCallback
    );

    // Pan监听任务
    this.panCallback = (info: GestureTriggerInfo) => {
      if (info.event?.target?.id === 'pan-area') {
        this.panCount++;
        this.lastAction = '平移';
        this.lastArea = 'Pan区域';
      }
    };
    observer.addGlobalGestureListener(
      GestureListenerType.PAN,
      {
        actionPhases: [GestureActionPhase.WILL_START, GestureActionPhase.WILL_END]
      },
      this.panCallback
    );

    // LongPress监听任务
    this.longPressCallback = (info: GestureTriggerInfo) => {
      if (info.event?.target?.id === 'longpress-area') {
        this.longPressCount++;
        this.lastAction = '长按';
        this.lastArea = 'LongPress区域';
      }
    };
    observer.addGlobalGestureListener(
      GestureListenerType.LONG_PRESS,
      {
        actionPhases: [GestureActionPhase.WILL_START, GestureActionPhase.WILL_END]
      },
      this.longPressCallback
    );
  }

  private removeGlobalListeners() {
    const observer = this.getUIContext().getUIObserver();
// 0、2、1分别表示Tap、Pan和LongPress手势类型，用于移除对应的全局监听
    if (this.tapCallback) {
      observer.removeGlobalGestureListener(GestureListenerType.TAP, this.tapCallback);
    }
    if (this.panCallback) {
      observer.removeGlobalGestureListener(GestureListenerType.PAN, this.panCallback);
    }
    if (this.longPressCallback) {
      observer.removeGlobalGestureListener(GestureListenerType.LONG_PRESS, this.longPressCallback);
    }
  }

  build() {
    Column() {
      // 手势数据统计面板
      Row({ space: 30 }) {
        Column() {
          Text('点击次数：').fontSize(16)
          Text(`${this.tapCount}`).fontSize(24).fontColor('#FF6B81')
        }
        Column() {
          Text('平移次数：').fontSize(16)
          Text(`${this.panCount}`).fontSize(24).fontColor('#7BED9F')
        }
        Column() {
          Text('长按次数：').fontSize(16)
          Text(`${this.longPressCount}`).fontSize(24).fontColor('#70A1FF')
        }
      }
      .margin(10)

      Text(`最后动作：${this.lastAction}（${this.lastArea}）`)
        .fontSize(18)
        .margin(10)

      // 手势区域
      Row() {
        Text('Tap区域').fontSize(18)
      }
      .id('tap-area')
      .width('90%')
      .height(120)
      .margin(10)
      .border({ width: 2, color: '#FF6B81' })
      .justifyContent(FlexAlign.Center)
      .gesture(TapGesture().onAction((event: GestureEvent) => {
        // 具体实现内容
      }))

      Row() {
        Text('Pan区域').fontSize(18)
      }
      .id('pan-area')
      .width('90%')
      .height(120)
      .margin(10)
      .border({ width: 2, color: '#7BED9F' })
      .justifyContent(FlexAlign.Center)
      .gesture(
        PanGesture()
          .onActionStart((event: GestureEvent) => {
            // 具体实现内容
          })
          .onActionEnd((event: GestureEvent) => {
            // 具体实现内容
          })
      )

      Row() {
        Text('LongPress区域').fontSize(18)
      }
      .id('longpress-area')
      .width('90%')
      .height(120)
      .margin(10)
      .border({ width: 2, color: '#70A1FF' })
      .justifyContent(FlexAlign.Center)
      .gesture(
        LongPressGesture()
          .onAction((event: GestureEvent) => {
            // 具体实现内容
          })
          .onActionEnd((event: GestureEvent) => {
            // 具体实现内容
          })
      )
    }
    .width('100%')
    .height('100%')
  }
}
```

## off('navDestinationUpdate')

```TypeScript
off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<observer.NavDestinationInfo>): void
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdate'. |
| options | { navigationId: ResourceStr } | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and navigation ID will be removed. |

**示例**

参考[on('navDestinationUpdate')](#onnavdestinationupdate)接口示例。

## off('navDestinationUpdate')

```TypeScript
off(type: 'navDestinationUpdate', callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('navDestinationUpdate')](#onnavdestinationupdate)接口示例。

## off('navDestinationUpdateByUniqueId')

```TypeScript
off(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | 是 | The uniqueId of the navigation. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('navDestinationUpdateByUniqueId')](#onnavdestinationupdatebyuniqueid)接口示例。

## off('scrollEvent')

```TypeScript
off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |

**示例**

参考[on('scrollEvent')](#onscrollevent)接口示例。

## off('scrollEvent')

```TypeScript
off(type: 'scrollEvent', callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('scrollEvent')](#onscrollevent)接口示例。

## off('routerPageUpdate')

```TypeScript
off(type: 'routerPageUpdate', callback?: Callback<observer.RouterPageInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | The type of event to remove the listener for. Must be 'routerPageUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('routerPageUpdate')](#onrouterpageupdate)接口示例。

## off('densityUpdate')

```TypeScript
off(type: 'densityUpdate', callback?: Callback<observer.DensityInfo>): void
```

取消监听屏幕像素密度的变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销该[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)下所有屏幕像素密度变化事件监听。 |

**示例**

参考[on('densityUpdate')](#ondensityupdate)接口示例。

## off('willDraw')

```TypeScript
off(type: 'willDraw', callback?: Callback<void>): void
```

取消监听每一帧绘制指令下发情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 需要被注销的回调函数。不传参数时，取消所有绘制指令下发事件的监听回调。 |

**示例**

参考[on('willDraw')](#onwilldraw)接口示例。

## off('didLayout')

```TypeScript
off(type: 'didLayout', callback?: Callback<void>): void
```

取消监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 需要被注销的回调函数。不传参数时，取消所有布局完成的监听回调。 |

**示例**

参考[on('didLayout')](#ondidlayout)接口示例。

## off('navDestinationSwitch')

```TypeScript
off(
    type: 'navDestinationSwitch',
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to remove the listener for. Must be 'navDestinationSwitch'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('navDestinationSwitch')](#onnavdestinationswitch)接口示例。

## off('navDestinationSwitch')

```TypeScript
off(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to remove the listener for. Must be 'navDestinationSwitch'. |
| observerOptions | [observer.NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | Options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('navDestinationSwitch')](#onnavdestinationswitch)接口示例。

## off('willClick')

```TypeScript
off(type: 'willClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called before clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to remove the listener for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## off('didClick')

```TypeScript
off(type: 'didClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called after clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to remove the listener for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## off('willClick')

```TypeScript
off(type: 'willClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called before tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to remove the listener for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## off('didClick')

```TypeScript
off(type: 'didClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called after tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to remove the listener for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## off('beforePanStart')

```TypeScript
off(type: 'beforePanStart', callback?: PanListenerCallback): void
```

取消[on('beforePanStart')](#onbeforepanstart)监听Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行前的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanStart' | 是 | 监听事件，固定为'beforePanStart'，即Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行前的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行前的指令下发监听回调。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## off('beforePanEnd')

```TypeScript
off(type: 'beforePanEnd', callback?: PanListenerCallback): void
```

取消[on('beforePanEnd')](#onbeforepanend)监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行前的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | 是 | 监听事件，固定为'beforePanEnd'，即Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行前的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行前的指令下发监听回调。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## off('afterPanStart')

```TypeScript
off(type: 'afterPanStart', callback?: PanListenerCallback): void
```

取消[on('afterPanStart')](#onafterpanstart)监听Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行后的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanStart' | 是 | 监听事件，固定为'afterPanStart'，即Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行后的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行后的指令下发监听回调。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## off('afterPanEnd')

```TypeScript
off(type: 'afterPanEnd', callback?: PanListenerCallback): void
```

取消[on('afterPanEnd')](#onafterpanend)监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行后的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | 是 | 监听事件，固定为'afterPanEnd'，即Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行后的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行后的指令下发监听回调。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## off('tabContentUpdate')

```TypeScript
off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

**示例**

参考[on('tabContentUpdate')](#ontabcontentupdate)接口示例。

## off('tabContentUpdate')

```TypeScript
off(type: 'tabContentUpdate', callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

**示例**

参考[on('tabContentUpdate')](#ontabcontentupdate)接口示例。

## off('tabChange')

```TypeScript
off(type: 'tabChange', config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 `on()` 注册的回调函数。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要移除监听的事件类型。必须是 'tabChange'。 |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 否 | 要移除的回调函数。如果未提供该参数，则将移除该tabs id的所有'tabChange'无感监听回调函数。 |

**示例**

参考[on('tabChange')](#ontabchange)接口示例。

## off('tabChange')

```TypeScript
off(type: 'tabChange', callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 `on()` 注册的回调函数。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要移除监听的事件类型。必须是 'tabChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 否 | 要移除的回调函数。如果未提供该参数，则将移除所有tabs的所有'tabChange'无感监听回调函数。 |

**示例**

参考[on('tabChange')](#ontabchange)接口示例。

## off('windowSizeLayoutBreakpointChange')

```TypeScript
off(type: 'windowSizeLayoutBreakpointChange', callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

移除之前注册的窗口尺寸布局断点变化回调函数。如果未提供回调函数参数，将移除指定上下文的所有回调函数。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | 是 | 监听事件，固定为'windowSizeLayoutBreakpointChange'，用于监听窗口尺寸布局断点发生改变。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-c.md)&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销该[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)下所有窗口尺寸布局断点变化事件监听。 |

**示例**

参考[on('windowSizeLayoutBreakpointChange')](#onwindowsizelayoutbreakpointchange)接口示例。

## off('nodeRenderState')

```TypeScript
off(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void
```

取消监听节点渲染状态发生变化的callback回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | 是 | 监听事件，固定为'nodeRenderState'，即节点渲染状态变化指令下发情况。 |
| nodeIdentity | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 是 | 节点标识。 |
| callback | [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消该节点所有的渲染状态变化指令下发监听回调。 |

**示例**

参考[on('nodeRenderState')](#onnoderenderstate)接口示例。

## off('textChange')

```TypeScript
off(type: 'textChange', callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to remove the listener for. Must be 'textChange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('textChange')](#ontextchange)示例。

## off('textChange')

```TypeScript
off(type: 'textChange', identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to remove the listener for. Must be 'textChange'. |
| identity | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | Identity options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

**示例**

参考[on('textChange')](#ontextchange)示例。

## offNavDestinationSizeChange

```TypeScript
offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

**示例**

参考[onNavDestinationSizeChange](#onnavdestinationsizechange)接口示例。

## offNavDestinationSizeChangeByUniqueId

```TypeScript
offNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChangeByUniqueId接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | number | 是 | 希望监听的NavDestination所属的Navigation的唯一ID，可以通过 [queryNavigationInfo](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md#querynavigationinfo)获取。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有指定了相同navigationUniqueId的回调函数。 |

**示例**

参考[onNavDestinationSizeChangeByUniqueId](#onnavdestinationsizechangebyuniqueid)接口示例。

## offRouterPageSizeChange

```TypeScript
offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void
```

移除使用onRouterPageSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

**示例**

参考[onRouterPageSizeChange](#onrouterpagesizechange)接口示例。

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void
```

取消监听Swiper内容的切换事件。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

**示例**

参考[onSwiperContentUpdate](#onswipercontentupdate)接口示例。

<a id="offswipercontentupdate-1"></a>

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void
```

取消通过Swiper组件id监听的Swiper内容切换事件。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | 指定监听的Swiper组件信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

**示例**

参考[onSwiperContentUpdate](#onswipercontentupdate)接口示例。

## on('navDestinationUpdate')

```TypeScript
on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<observer.NavDestinationInfo>): void
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | Event type. The value is fixed at **'navDestinationUpdate'**, which indicates the state change event<br>of the **NavDestination** component. |
| options | { navigationId: ResourceStr } | 是 | ID of the target **NavDestination** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | Callback used to return the current<br>state of the **NavDestination** component. |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('navDestinationUpdate', options, callback)
// uiObserver.off('navDestinationUpdate', options, callback)

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    // 添加监听，指定Navigation的id
    this.getUIContext().getUIObserver().on('navDestinationUpdate', { navigationId: 'testId' }, (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    // 取消监听，不选择回调时，取消所有监听的回调
    this.getUIContext().getUIObserver().off('navDestinationUpdate', { navigationId: 'testId' });
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // 将PageOne的NavDestination入栈
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .id('testId')
      .title('Navigation')
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('navDestinationUpdate')

```TypeScript
on(type: 'navDestinationUpdate', callback: Callback<observer.NavDestinationInfo>): void
```

Subscribes to status changes of this **NavDestination** component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | Event type. The value is fixed at **'navDestinationUpdate'**,<br>which indicates the state change event of the **NavDestination** component. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | Callback used to return the current state of<br>the **NavDestination** component. |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('navDestinationUpdate', callback)
// uiObserver.off('navDestinationUpdate', callback)

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    // 添加监听
    this.getUIContext().getUIObserver().on('navDestinationUpdate', (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    // 取消监听，不选择回调时，取消所有监听的回调
    this.getUIContext().getUIObserver().off('navDestinationUpdate');
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // 将PageOne的NavDestination入栈
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .title('Navigation')
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('navDestinationUpdateByUniqueId')

```TypeScript
on(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

Registers a callback function to be called when the navigation destination is updated.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | 是 | The type of event to listen for. Must be 'navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | 是 | The uniqueId of the navigation. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | The callback function to be called when the navigation destination is updated. |

**示例**

通过[Navigation](../arkui-ts/ts-basic-components-navigation.md)的uniqueId，可以监听[NavDestination](../arkui-ts/ts-basic-components-navdestination.md)组件的状态变化。

```TypeScript
// Index.ets
// 演示on('navDestinationUpdateByUniqueId', navigationUniqueId, callback)
// off('navDestinationUpdateByUniqueId', navigationUniqueId, callback)

@Component
struct PageOne {
  private text = '';
  private uniqueId = -1;
  aboutToAppear() {
    // 获取Navigation的uniqueId
    let navigationUniqueId = this.queryNavigationInfo()?.uniqueId;
    if (navigationUniqueId) {
      this.uniqueId = navigationUniqueId.valueOf();
    }
    this.text = JSON.stringify(this.uniqueId);
    // 添加监听，指定Navigation的uniqueId
    this.getUIContext().getUIObserver().on('navDestinationUpdateByUniqueId', this.uniqueId, (info) => {
      console.info('NavDestination state update navigationId', JSON.stringify(info));
    });
  }
  aboutToDisappear() {
    // 取消监听，不选择回调时，取消所有监听的回调
    this.getUIContext().getUIObserver().off('navDestinationUpdateByUniqueId', this.uniqueId);
  }
  build() {
    NavDestination() {
      Text('pageOne')
      Text('navigationUniqueId是：' + this.text)
        .width('80%')
        .height(50)
        .margin(50)
        .fontSize(20)
    }.title('pageOne')
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // 将PageOne的NavDestination入栈
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .id('testId')
      .title('Navigation')
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('scrollEvent')

```TypeScript
on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 是 | The callback function to be called when the scroll event start or stop. |

**示例**

参考[on('scrollEvent')](#onscrollevent)接口示例。

## on('scrollEvent')

```TypeScript
on(type: 'scrollEvent', callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 是 | The callback function to be called when the scroll event start or stop. |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('scrollEvent', callback)
// uiObserver.off('scrollEvent', callback)
// uiObserver.on('scrollEvent', options, callback)
// uiObserver.off('scrollEvent', options, callback)

import { UIObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  observer: UIObserver = this.getUIContext().getUIObserver();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7];

  build() {
    Column() {
      Column() {
        Scroll(this.scroller) {
          Column() {
            ForEach(this.arr, (item: number) => {
              Text(item.toString())
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }, (item: number) => item.toString())
          }.width('100%')
        }
        .id('testId')
        .height('80%')
      }
      .width('100%')

      Row() {
        Button('UIObserver on')
          .onClick(() => {
            // 添加监听
            this.observer.on('scrollEvent', (info) => {
              console.info('scrollEventInfo', JSON.stringify(info));
            });
          })
        Button('UIObserver off')
          .onClick(() => {
            // 取消监听，不选择回调时，取消所有监听的回调
            this.observer.off('scrollEvent');
          })
      }

      Row() {
        Button('UIObserverWithId on')
          .onClick(() => {
            // 添加监听，指定滚动组件的id
            this.observer.on('scrollEvent', { id: 'testId' }, (info) => {
              console.info('scrollEventInfo', JSON.stringify(info));
            });
          })
        Button('UIObserverWithId off')
          .onClick(() => {
            // 取消监听，不选择回调时，取消所有监听的回调
            this.observer.off('scrollEvent', { id: 'testId' });
          })
      }
    }
    .height('100%')
  }
}
```

## on('routerPageUpdate')

```TypeScript
on(type: 'routerPageUpdate', callback: Callback<observer.RouterPageInfo>): void
```

Unsubscribes to state changes of the page in the router.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | Event type.<br>The value is fixed at 'routerPageUpdate', which indicates the state change event of the page in the router. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | Callback to be unregistered. |

**示例**

```TypeScript
// PageOne.ets

@Entry
@Component
struct PageOne {
  build() {
    Column() {
      Text('pageOne')
    }
  }
}
```

```TypeScript
// Index.ets
// 演示uiObserver.on('routerPageUpdate', callback)
// uiObserver.off('routerPageUpdate', callback)

@Entry
@Component
struct Index {
  aboutToAppear() {
    // 添加监听
    this.getUIContext().getUIObserver().on('routerPageUpdate', (info) => {
      console.info('router page update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    // 取消监听，不选择回调时，取消所有监听的回调
    this.getUIContext().getUIObserver().off('routerPageUpdate');
  }

  build() {
    Column() {
      Button('pushUrl').onClick(() => {
        // router跳转到PageOne.ets页面
        this.getUIContext().getRouter().pushUrl({ url: 'pages/PageOne' });
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('densityUpdate')

```TypeScript
on(type: 'densityUpdate', callback: Callback<observer.DensityInfo>): void
```

监听屏幕像素密度变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | 是 | 回调函数。携带[DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)，返回变化后的屏幕像素密度。 |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('densityUpdate', callback)
// uiObserver.off('densityUpdate', callback)

import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = '未注册监听';

  // 定义监听回调函数
  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = '变化后的DPI：' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button('注册屏幕像素密度变化监听')
        .margin({ bottom: 10 })
        .onClick(() => {
          this.message = '已注册监听';
          // 添加监听
          this.getUIContext().getUIObserver().on('densityUpdate', this.densityUpdateCallback);
        })
      Button('解除注册屏幕像素密度变化监听')
        .onClick(() => {
          this.message = '未注册监听';
          // 取消监听
          this.getUIContext().getUIObserver().off('densityUpdate', this.densityUpdateCallback);
        })
    }
  }
}
```

## on('willDraw')

```TypeScript
on(type: 'willDraw', callback: Callback<void>): void
```

监听每一帧绘制指令下发情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('willDraw', callback)
// uiObserver.off('willDraw', callback)

@Entry
@Component
struct Index {
  // 定义监听回调函数
  willDrawCallback = () => {
    console.info('willDraw指令下发');
  }

  build() {
    Column() {
      Button('注册绘制指令下发监听')
        .margin({ bottom: 10 })
        .onClick(() => {
          // 添加监听
          this.getUIContext().getUIObserver().on('willDraw', this.willDrawCallback);
        })
      Button('解除注册绘制指令下发监听')
        .onClick(() => {
          // 取消监听
          this.getUIContext().getUIObserver().off('willDraw', this.willDrawCallback);
        })
    }
  }
}
```

## on('didLayout')

```TypeScript
on(type: 'didLayout', callback: Callback<void>): void
```

监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('didLayout', callback)
// uiObserver.off('didLayout', callback)

@Entry
@Component
struct Index {
  // 定义监听回调函数
  didLayoutCallback = () => {
    console.info('layout布局完成');
  }

  build() {
    Column() {
      Button('注册布局完成监听')
        .margin({ bottom: 10 })
        .onClick(() => {
          // 添加监听
          this.getUIContext().getUIObserver().on('didLayout', this.didLayoutCallback);
        })
      Button('解除注册布局完成监听')
        .onClick(() => {
          // 取消监听
          this.getUIContext().getUIObserver().off('didLayout', this.didLayoutCallback);
        })
    }
  }
}
```

## on('navDestinationSwitch')

```TypeScript
on(
    type: 'navDestinationSwitch',
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to listen for. Must be 'navDestinationSwitch'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 是 | The callback function to be called when the navigation switched to a new navDestination. |

**示例**

```TypeScript
// Index.ets
// 演示UIObserver.on('navDestinationSwitch', callback)
// UIObserver.off('navDestinationSwitch', callback)

import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

// 定义监听回调函数
const callbackFunc = (info: uiObserver.NavDestinationSwitchInfo) => {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`);
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    let obs = this.getUIContext().getUIObserver();
    // 添加监听
    obs.on('navDestinationSwitch', callbackFunc);
  }

  aboutToDisappear() {
    let obs = this.getUIContext().getUIObserver();
    // 取消监听
    obs.off('navDestinationSwitch', callbackFunc);
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // 将PageOne的NavDestination入栈
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .title("Navigation")
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('navDestinationSwitch')

```TypeScript
on(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to listen for. Must be 'navDestinationSwitch'. |
| observerOptions | [observer.NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | Options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 是 | The callback function to be called when the navigation switched to a new navDestination. |

**示例**

```TypeScript
// Index.ets
// 演示UIObserver.on('navDestinationSwitch', observerOptions, callback)
// UIObserver.off('navDestinationSwitch', observerOptions, callback)

import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text('pageOne')
    }.title('pageOne')
  }
}

// 定义监听回调函数
function callbackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`);
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  pageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    let obs = this.getUIContext().getUIObserver();
    // 添加监听，指定Navigation的id
    obs.on('navDestinationSwitch', { navigationId: 'myNavId' }, callbackFunc);
  }

  aboutToDisappear() {
    let obs = this.getUIContext().getUIObserver();
    // 取消监听
    obs.off('navDestinationSwitch', { navigationId: 'myNavId' }, callbackFunc);
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button('push').onClick(() => {
          // 将PageOne的NavDestination入栈
          this.stack.pushPath({ name: 'pageOne' });
        })
      }
      .id("myNavId")
      .title("Navigation")
      .navDestination(this.pageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

## on('willClick')

```TypeScript
on(type: 'willClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called before clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to listen for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## on('didClick')

```TypeScript
on(type: 'didClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called after clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to listen for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## on('willClick')

```TypeScript
on(type: 'willClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called before tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to listen for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('willClick', callback)
// uiObserver.off('willClick', callback)
// uiObserver.on('didClick', callback)
// uiObserver.off('didClick', callback)

// 定义监听回调函数
const willClickGestureCallback = (event: GestureEvent, node?: FrameNode) => {
  console.info('Example willClickCallback GestureEvent is called');
}

const willClickCallback = (event: ClickEvent, node?: FrameNode) => {
  console.info('Example willClickCallback ClickEvent is called');
}

const didClickGestureCallback = (event: GestureEvent, node?: FrameNode) => {
  console.info('Example didClickCallback GestureEvent is called');
}

const didClickCallback = (event: ClickEvent, node?: FrameNode) => {
  console.info('Example didClickCallback ClickEvent is called');
}

@Entry
@Component
struct ClickExample {
  @State clickCount: number = 0;
  @State tapGestureCount: number = 0;

  aboutToAppear(): void {
    // 添加监听
    let observer = this.getUIContext().getUIObserver();
    observer.on('willClick', willClickGestureCallback);
    observer.on('willClick', willClickCallback);
    observer.on('didClick', didClickGestureCallback);
    observer.on('didClick', didClickCallback);
  }

  aboutToDisappear(): void {
    // 取消监听
    let observer = this.getUIContext().getUIObserver();
    observer.off('willClick', willClickGestureCallback);
    observer.off('willClick', willClickCallback);
    // 如果不选择回调，则会取消所有监听的回调
    observer.off('didClick');
  }

  build() {
    Column() {
      /**
       * onClick和TapGesture在后端的处理是一致的
       * 所以无论是触发onClick还是触发TapGesture
       * on('willClick')两种类型入参的回调（GestureEvent和ClickEvent）都会被触发
       * 同理，on('didClick')的两种回调也会被触发
       */
      Column() {
        Text('Click Count: ' + this.clickCount)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .onClick((event: ClickEvent) => {
        this.clickCount++;
        console.info('Example Click event is called');
      })

      Column() {
        Text('TapGesture Count: ' + this.tapGestureCount)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .gesture(TapGesture({ count: 2 }).onAction((event: TapGestureEvent) => {
        this.tapGestureCount++;
        console.info('Example Click event is called');
      }))
    }
  }
}
```

## on('didClick')

```TypeScript
on(type: 'didClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called after tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to listen for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

**示例**

参考[on('willClick')](#onwillclick)接口示例。

## on('beforePanStart')

```TypeScript
on(type: 'beforePanStart', callback: PanListenerCallback): void
```

监听Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件，在[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanStart' | 是 | 监听事件，固定为'beforePanStart'，用于监听Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行前的指令下发情况，所注册回调将于Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件触发前触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('beforePanStart', callback)
// uiObserver.off('beforePanStart', callback)
// uiObserver.on('afterPanStart', callback)
// uiObserver.off('afterPanStart', callback)
// uiObserver.on('beforePanEnd', callback)
// uiObserver.off('beforePanEnd', callback)
// uiObserver.on('afterPanEnd', callback)
// uiObserver.off('afterPanEnd', callback)

// 在页面Component中使用
let TEST_TAG: string = 'node';

// 定义监听回调函数
const callbackFunc = () => {
  console.info('on == beforePanStart');
}

const afterPanCallBack = () => {
  console.info('on == afterPanStart');
}

const beforeEndCallBack = () => {
  console.info('on == beforeEnd');
}

const afterEndCallBack = () => {
  console.info('on == afterEnd');
}

const beforeStartCallBack = () => {
  console.info('on == beforeStartCallBack');
}

const panGestureCallBack = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => {
  TEST_TAG = 'panGestureEvent';
  console.info('===' + TEST_TAG + '=== event.repeat is ' + event.repeat);
  console.info('===' + TEST_TAG + '=== event target is ' + event.target.id);
  TEST_TAG = 'panGestureCurrent';
  console.info('===' + TEST_TAG + '=== current.getTag() is ' + current.getTag());
  TEST_TAG = 'panGestureNode';
  console.info('===' + TEST_TAG + '=== node?.getId() is ' + node?.getId());
}


@Entry
@Component
struct PanExample {
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State positionX: number = 0;
  @State positionY: number = 0;
  private panOption: PanGestureOptions = new PanGestureOptions({direction: PanDirection.All });

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 添加监听
    observer.on('beforePanStart', callbackFunc);
    observer.on('beforePanStart', panGestureCallBack);
    observer.on('beforePanStart', beforeStartCallBack);
    observer.on('afterPanStart', afterPanCallBack);
    observer.on('beforePanEnd', beforeEndCallBack);
    observer.on('afterPanEnd', afterEndCallBack);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 取消监听
    observer.off('beforePanStart', callbackFunc);
    observer.off('beforePanStart');
    observer.off('afterPanStart', afterPanCallBack);
    observer.off('beforePanEnd');
    observer.off('afterPanEnd');
  }

  build() {
    Column() {
      Column() {
        Text('PanGesture :\nX: ' + this.offsetX + '\n' + 'Y: ' + this.offsetY)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .translate({ x: this.offsetX, y: this.offsetY, z: 0 })
      .id('columnOuter')
      .gesture(
        PanGesture(this.panOption)
          .onActionStart((event: GestureEvent) => {
            console.info('Pan start');
          })
          .onActionUpdate((event: GestureEvent) => {
            if (event) {
              this.offsetX = this.positionX + event.offsetX;
              this.offsetY = this.positionY + event.offsetY;
            }
          })
          .onActionEnd((event: GestureEvent) => {
            this.positionX = this.offsetX;
            this.positionY = this.offsetY;
            console.info('Pan end');
            }))
          }
  }
}
```

## on('beforePanEnd')

```TypeScript
on(type: 'beforePanEnd', callback: PanListenerCallback): void
```

监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行前的指令下发情况，在[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | 是 | 监听事件，固定为'beforePanEnd'，用于监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行前的指令下发情况，所注册回调将于Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件触发前触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## on('afterPanStart')

```TypeScript
on(type: 'afterPanStart', callback: PanListenerCallback): void
```

监听Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行后的指令下发情况，在[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanStart' | 是 | 监听事件，固定为'afterPanStart'，用于监听Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件执行后的指令下发情况，所注册回调将于Pan手势[onActionStart](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionstart)事件触发后触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## on('afterPanEnd')

```TypeScript
on(type: 'afterPanEnd', callback: PanListenerCallback): void
```

监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行后的指令下发情况，在[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | 是 | 监听事件，固定为'afterPanEnd'，用于监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件执行后的指令下发情况，所注册回调将于Pan手势[onActionEnd](../arkts-components/arkts-arkui-tapgesture-comp-pangestureinterface-i.md#onactionend)事件触发后触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-tapgesture-comp-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

**示例**

参考[on('beforePanStart')](#onbeforepanstart)接口示例。

## on('tabContentUpdate')

```TypeScript
on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to listen for. Must be 'tabContentUpdate'. |
| options | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | The callback function to be called when the tabContent show or hide. |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('tabContentUpdate', options, callback)
// uiObserver.off('tabContentUpdate', options, callback)

import { uiObserver } from '@kit.ArkUI';

// 定义监听回调函数
function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 添加监听，指定Tabs的id
    observer.on('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 取消监听
    observer.off('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')
    }.width('100%')
  }
}
```

## on('tabContentUpdate')

```TypeScript
on(type: 'tabContentUpdate', callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to listen for. Must be 'tabContentUpdate'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | The callback function to be called when the tabContent is showed or hidden. |

**示例**

```TypeScript
// Index.ets
// 演示uiObserver.on('tabContentUpdate', callback)
// uiObserver.off('tabContentUpdate', callback)

import { uiObserver } from '@kit.ArkUI';

// 定义监听回调函数
const callbackFunc = (info: uiObserver.TabContentInfo) => {
  console.info('tabContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 添加监听
    observer.on('tabContentUpdate', callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 取消监听
    observer.off('tabContentUpdate', callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')
    }.width('100%')
  }
}
```

## on('tabChange')

```TypeScript
on(type: 'tabChange', config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要监听的事件类型。必须是 'tabChange'。 |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | 回调函数，当 tabContent 显示或隐藏时被调用。 |

**示例**

```TypeScript
// Index.ets
// 演示监听id为'tabsId'的Tabs组件页签的切换事件。
// Tabs组件页签初始化的时候，会监听到第0页页签的显示事件，页签对应id为'tabContentId0'；滑动一下，会监听到第0页的页签隐藏、id为'tabContentId1'的第1页页签显示事件。
import { uiObserver } from '@kit.ArkUI';

// 定义监听回调函数
function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabChange', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 添加监听，指定Tabs的id
    observer.on('tabChange', { id: 'tabsId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 取消监听
    observer.off('tabChange', { id: 'tabsId' }, callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')

      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId5')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId6')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId7')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId8')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
    }.width('100%')
  }
}
```

## on('tabChange')

```TypeScript
on(type: 'tabChange', callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要监听的事件类型。必须是 'tabChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TabContentInfo](arkts-arkui-uiobserver-tabcontentinfo-i.md)&gt; | 是 | 回调函数，当 tabContent 显示或隐藏时调用。 |

**示例**

```TypeScript
// Index.ets
// 演示监听Tabs组件页签的切换事件。
// 此用例同时监听id为'tabsId1'、'tabsId2'的两个Tabs组件。
// 两个Tabs组件初始化时，会监听到第0页页签的显示事件，页签对应id分别为'tabContentId0'、'tabContentId5'。
// 在id为'tabsId1'的Tabs组件上滑动一下，会监听到第0页的页签隐藏、id为'tabContentId1'的第1页页签显示事件。
import { uiObserver } from '@kit.ArkUI';

// 定义监听回调函数
function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabChange', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 添加监听
    observer.on('tabChange', callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    // 取消监听
    observer.off('tabChange', callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId1')

      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId5')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId6')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId7')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId8')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId2')
    }.width('100%')
  }
}
```

## on('windowSizeLayoutBreakpointChange')

```TypeScript
on(type: 'windowSizeLayoutBreakpointChange', callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

注册窗口尺寸布局断点变化的回调函数。该方法用于监听窗口尺寸断点变化，可用于根据窗口尺寸自适应调整UI布局。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | 是 | 监听事件，固定为'windowSizeLayoutBreakpointChange'，用于监听窗口尺寸布局断点发生改变。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.WindowSizeLayoutBreakpointInfo](arkts-arkui-uiobserver-windowsizelayoutbreakpointinfo-c.md)&gt; | 是 | 回调函数。携带WindowSizeLayoutBreakpointinfo，包含窗口宽度和高度所在的布局断点枚举。 |

**示例**

该示例展示添加和取消监听窗口尺寸布局断点变化的方法。

```TypeScript
import { uiObserver, window } from '@kit.ArkUI';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  private changeOrientation(isLandscape: boolean) {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    window.getLastWindow(context).then((lastWindow) => {
      lastWindow.setPreferredOrientation(isLandscape ? window.Orientation.LANDSCAPE : window.Orientation.PORTRAIT);
    });
  }

  @State message: string = '';
  @State widthBreakpoint: WidthBreakpoint = WidthBreakpoint.WIDTH_SM;
  @State heightBreakpoint: HeightBreakpoint = HeightBreakpoint.HEIGHT_SM;
  winSizeLayoutBreakpointCallback = (info: uiObserver.WindowSizeLayoutBreakpointInfo) => {
    this.widthBreakpoint = info.widthBreakpoint;
    this.heightBreakpoint = info.heightBreakpoint;
    this.message = 'widthBpt:' + this.widthBreakpoint.toString() + 'heightBpt:' + this.heightBreakpoint.toString();
  }

  build() {
    Column() {
      Text(this.message)
      Button('注册窗口尺寸布局断点变化监听')
        .onClick(() => {
          this.getUIContext()
            .getUIObserver()
            .on('windowSizeLayoutBreakpointChange', this.winSizeLayoutBreakpointCallback);
        })
      Button('解除窗口尺寸布局断点变化监听')
        .onClick(() => {
          this.getUIContext()
            .getUIObserver()
            .off('windowSizeLayoutBreakpointChange', this.winSizeLayoutBreakpointCallback);
        })
      Button("竖屏").onClick(() => {
        this.changeOrientation(false);
      })
      Button("横屏").onClick(() => {
        this.changeOrientation(true);
      })
    }
  }
}
```

## on('nodeRenderState')

```TypeScript
on(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void
```

注册一个回调函数，以便在特定节点的渲染状态发生变化时调用，当注册成功时，此回调将立即执行一次。

注意节点数量的限制。出于性能考虑，在单个UI实例中，注册节点太多，将会抛出异常。

通常，当组件被移动到屏幕外时，会收到RENDER_OUT的通知。但在某些情况下，即使组件移动到屏幕外也不会触发RENDER_OUT通知。例如，具有缓存功能的组件Swiper，即使[cachedCount](../arkts-components/arkts-arkui-swiper-comp-attribute.md#cachedcount-1)属性中的参数isShown配置为true，也不会触发RENDER_OUT通知。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | 是 | 监听事件，固定为'nodeRenderState'，用于监听节点渲染状态发生改变。 |
| nodeIdentity | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 是 | 节点标识。 |
| callback | [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 是 | 回调函数。可以获得节点渲染状态改变事件的[NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [161001](../errorcode-node-render-monitor.md#161001-监听渲染状态的节点数超过限制) | The count of nodes monitoring render state is over the limitation. |

**示例**

该示例展示了如何对目标组件添加监听和取消监听。当向左滑动，被监听组件从屏幕消失，会收到RENDER_OUT的通知，然后向右滑动，被监听组件重新出现在屏幕上，会收到RENDER_IN通知。

```TypeScript
// Index.ets
// 演示uiObserver.on('nodeRenderState', nodeIdentity, callback)
// uiObserver.off('nodeRenderState', nodeIdentity, callback)

// 在页面Component中使用
import { NodeRenderState } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  @State notice: string = "";
  private controller: TabsController = new TabsController();

  @Builder
  tabBuilder(index: number, name: string) {
    Column() {
      Text(name)
        .fontColor(this.selectedIndex === index ? this.selectedFontColor : this.fontColor)
        .fontSize(16)
        .fontWeight(this.selectedIndex === index ? 500 : 400)
        .lineHeight(22)
        .margin({ top: 17, bottom: 7 })
      Divider()
        .strokeWidth(2)
        .color('#007DFF')
        .opacity(this.selectedIndex === index ? 1 : 0)
    }.width('100%')
  }

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, index: this.currentIndex, controller: this.controller }) {
        TabContent() {
          Column() {
            Column() {
              Button("被监听节点").margin({ top: 5 }).id("button_1")
              Button("添加监听").margin({ top: 5 }).onClick(() => {
                let node: FrameNode | null = this.getUIContext().getFrameNodeById("button_1");
                if (node) {
                  let observer = this.getUIContext().getUIObserver();
                  // 添加监听
                  observer.on("nodeRenderState", node?.getUniqueId(), (state: NodeRenderState, node?: FrameNode) => {
                    // 根据节点状态修改通知信息
                    if (state === 0) {
                      this.notice = "RENDER_IN";
                    } else {
                      this.notice = "RENDER_OUT";
                    }
                    console.info("节点状态发生改变，当前状态：", state);
                  });
                }
              })
              Button("取消监听").margin({ top: 5 }).onClick(() => {
                let node: FrameNode | null = this.getUIContext().getFrameNodeById("button_1");
                if (node) {
                  let observer = this.getUIContext().getUIObserver();
                  // 取消监听，不选择回调时，取消所有监听的回调
                  observer.off("nodeRenderState", node?.getUniqueId());
                }
                this.notice = "";
              })
            }
          }.width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar(this.tabBuilder(0, 'green'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar(this.tabBuilder(1, 'blue'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar(this.tabBuilder(2, 'yellow'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar(this.tabBuilder(3, 'pink'))
      }
      .vertical(false)
      .barMode(BarMode.Fixed)
      .barWidth(360)
      .barHeight(56)
      .animationDuration(400)
      .onChange((index: number) => {
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        if (index === targetIndex) {
          return;
        }
        this.selectedIndex = targetIndex;
      })
      .width(360)
      .height(296)
      .margin({ top: 52 })
      .backgroundColor('#F1F3F5')

      Text(`收到的通知：${this.notice}`)
        .fontSize(20)
        .margin(10)
    }.width('100%')
  }
}
```

## on('textChange')

```TypeScript
on(type: 'textChange', callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to listen for. Must be 'textChange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | 是 | The callback function to be called when text field's content is changed. |

**示例**

```TypeScript
import { UIObserver } from '@kit.ArkUI';

@Entry
@Component
struct TextUiObserver {
  observer: UIObserver = this.getUIContext().getUIObserver();
  build() {
    Column() {
      TextArea({ text: 'Hello World TextArea' })
        .width(336)
        .height(56)
        .margin({bottom:5})
        .backgroundColor('#FFFFFF')
        .id('TestId1')
      TextInput({ text: 'Hello World TextInput' })
        .width(336)
        .height(56)
        .margin({bottom:5})
        .backgroundColor('#FFFFFF')
        .id('TestId2')
      Search({ value: 'Hello World Search' })
        .width(336)
        .height(56)
        .margin({bottom:5})
        .backgroundColor('#FFFFFF')
        .id('TestId3')
      Row() {
        // 开启全局监听
        Button('UIObserver on')
          .onClick(() => {
            this.observer.on('textChange', (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })
        // 关闭全局监听
        Button('UIObserver off')
          .onClick(() => {
            this.observer.off('textChange');
          })
      }.margin({bottom:5})
      // 开启和关闭指定ID的局部监听
      Row() {
        Button('UIObserver TestId1 on')
          .onClick(() => {
            this.observer.on('textChange', { id: 'TestId1' }, (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })

        Button('UIObserver TestId1 off')
          .onClick(() => {
            this.observer.off('textChange', { id: 'TestId1' });
          })
      }.margin({bottom:5})
      Row() {
        Button('UIObserver TestId2 on')
          .onClick(() => {
            this.observer.on('textChange', { id: "TestId2" }, (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })

        Button('UIObserver TestId2 off')
          .onClick(() => {
            this.observer.off('textChange', { id: "TestId2" });
          })
      }.margin({bottom:5})
      Row() {
        Button('UIObserver TestId3 on')
          .onClick(() => {
            this.observer.on('textChange', { id: "TestId3" }, (info) => {
              console.info('textChangeInfo', JSON.stringify(info));
            });
          })

        Button('UIObserver TestId3 off')
          .onClick(() => {
            this.observer.off('textChange', { id: "TestId3" });
          })
      }.margin({bottom:5})
    }.width('100%').height('100%').backgroundColor('#F1F3F5')
  }
}
```

## on('textChange')

```TypeScript
on(type: 'textChange', identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to listen for. Must be 'textChange'. |
| identity | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | Identity options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.TextChangeEventInfo](arkts-arkui-uiobserver-textchangeeventinfo-i.md)&gt; | 是 | The callback function to be called when the text field's content is changed. |

**示例**

参考[on('textChange')](#ontextchange)示例。

## onNavDestinationSizeChange

```TypeScript
onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当可见的NavDestination大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | 回调函数。携带NavDestinationInfo，返回NavDestination的信息。 |

**示例**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOneContent {
  destSizeCallback(info: uiObserver.NavDestinationInfo): void {
    console.info(`testTag destSize changeTo ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
  }

  aboutToAppear(): void {
    // 可以通过注册监听的方式获取NavDestination页面大小信息
    this.getUIContext().getUIObserver().onNavDestinationSizeChange(this.destSizeCallback);
  }

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offNavDestinationSizeChange(this.destSizeCallback);
  }

  build() {
    Column() {
      Button('queryDestSize').onClick(() => {
        // 也可以主动获取NavDestination页面大小信息
        let info = this.queryNavDestinationInfo();
        console.info(`testTag destSize: ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct PageOne {
  build() {
    NavDestination() {
      PageOneContent()
    }
    .title('pageOne')
  }
}

@Entry
@Component
struct QueryNavDestinationSize {
  private stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack.pushPath({name: 'one'});
  }

  @Builder
  myPageMap(name: string) {
    PageOne()
  }

  build() {
    Navigation(this.stack) {
    }
    .width('100%')
    .height('100%')
    .navDestination(this.myPageMap)
    .hideNavBar(true)
  }
}
```

## onNavDestinationSizeChangeByUniqueId

```TypeScript
onNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当属于指定Navigation的可见NavDestination的大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | number | 是 | 希望监听NavDestination所属的Navigation的唯一ID，可以通过[queryNavigationInfo](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md#querynavigationinfo)获取。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | Callback to be removed. If no parameter is passed, all callbacks with the same **navigationUniqueId** setting are removed. |

**示例**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOneContent {
  private navUniqueId: number = 0;

  destSizeCallback(info: uiObserver.NavDestinationInfo): void {
    console.info(`testTag destSize changeTo ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
  }

  aboutToAppear(): void {
    let navInfo = this.queryNavigationInfo();
    if (navInfo && navInfo.uniqueId) {
      this.navUniqueId = navInfo.uniqueId;
      // 可以通过注册监听的方式获取NavDestination页面大小信息
      this.getUIContext().getUIObserver().onNavDestinationSizeChangeByUniqueId(this.navUniqueId, this.destSizeCallback);
    }
  }

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offNavDestinationSizeChangeByUniqueId(this.navUniqueId, this.destSizeCallback);
  }

  build() {
    Column() {
      Button('queryDestSize').onClick(() => {
        // 也可以主动获取NavDestination页面大小信息
        let info = this.queryNavDestinationInfo();
        console.info(`testTag destSize: ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct PageOne {
  build() {
    NavDestination() {
      PageOneContent()
    }
    .title('pageOne')
  }
}

@Entry
@Component
struct QueryNavDestinationSize {
  private stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack.pushPath({name: 'one'});
  }

  @Builder
  myPageMap(name: string) {
    PageOne()
  }

  build() {
    Navigation(this.stack) {
    }
    .width('100%')
    .height('100%')
    .navDestination(this.myPageMap)
    .hideNavBar(true)
  }
}
```

## onRouterPageSizeChange

```TypeScript
onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void
```

注册一个callback，当router可见页面尺寸发生变化时触发注册监听回调函数，当可见的Router页面大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[observer.RouterPageInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-observer.md)&gt; | 是 | 回调函数。携带RouterPageInfo，返回Router页面的信息。 |

**示例**

```TypeScript
import { uiObserver } from '@kit.ArkUI';

const myPageRouterPageSizeCallback = (info: uiObserver.RouterPageInfo): void => {
  console.info(`testTag pageSize changeTo ${(info && info.size) ? JSON.stringify(info.size) : 'NA'}`);
}

@Entry
@Component
struct QueryRouterPageSize {
  aboutToAppear(): void {
    // 可以通过注册监听的方式获取页面大小信息
    this.getUIContext().getUIObserver().onRouterPageSizeChange(myPageRouterPageSizeCallback);
  }

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offRouterPageSizeChange(myPageRouterPageSizeCallback);
  }

  build() {
    Column() {
      Button('querySize').onClick(() => {
        // 也可以主动获取页面大小信息
        let info = this.queryRouterPageInfo();
        console.info(`testTag pageSize: ${info && info.size ? JSON.stringify(info.size) : 'NA'}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void
```

监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

**示例**

```TypeScript
// Index.ets
import { SwiperContentInfo } from '@kit.ArkUI';

// 定义监听回调函数
const callbackFunc = (info: SwiperContentInfo) => {
  console.info('swiperContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();

  aboutToAppear(): void {
    // 注册swiperContentUpdate监听回调
    this.getUIContext().getUIObserver().onSwiperContentUpdate(callbackFunc);
  }

  aboutToDisappear(): void {
    // 取消swiperContentUpdate监听回调
    this.getUIContext().getUIObserver().offSwiperContentUpdate(callbackFunc);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        Column() {
          Text('SwiperItem1')
        }.width('100%').height('100%').backgroundColor('#00CB87')

        Column() {
          Text('SwiperItem2')
        }.width('100%').height('100%').backgroundColor('#007DFF')

        Column() {
          Text('SwiperItem3')
        }.width('100%').height('100%').backgroundColor('#FFBF00')

        Column() {
          Text('SwiperItem4')
        }.width('100%').height('100%').backgroundColor('#E67C92')
      }
      .width(360)
      .height(300)
    }.width('100%')
  }
}
```

<a id="onswipercontentupdate-1"></a>

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void
```

通过Swiper组件的id监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [observer.ObserverOptions](arkts-arkui-uiobserver-observeroptions-i.md) | 是 | 指定监听的Swiper组件信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

**示例**

```TypeScript
// Index.ets
import { SwiperContentInfo } from '@kit.ArkUI';

// 定义监听回调函数
function callbackFunc(info: SwiperContentInfo) {
  console.info('swiperContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct SwiperExample {
  private swiperController: SwiperController = new SwiperController();

  aboutToAppear(): void {
    // 通过id注册swiperContentUpdate监听回调
    this.getUIContext().getUIObserver().onSwiperContentUpdate({ id: 'swiperId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    // 通过id取消swiperContentUpdate监听回调
    this.getUIContext().getUIObserver().offSwiperContentUpdate({ id: 'swiperId' }, callbackFunc);
  }

  build() {
    Column({ space: 5 }) {
      Swiper(this.swiperController) {
        Column() {
          Text('SwiperItem1')
        }.width('100%').height('100%').backgroundColor('#00CB87')

        Column() {
          Text('SwiperItem2')
        }.width('100%').height('100%').backgroundColor('#007DFF')

        Column() {
          Text('SwiperItem3')
        }.width('100%').height('100%').backgroundColor('#FFBF00')

        Column() {
          Text('SwiperItem4')
        }.width('100%').height('100%').backgroundColor('#E67C92')
      }
      .id('swiperId')
      .width(360)
      .height(300)
    }.width('100%')
  }
}
```

## removeGlobalGestureListener

```TypeScript
removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void
```

移除某一手势监听器类型的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | 是 | 要移除监听器的事件类型。 |
| callback | [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 否 | 待移除的回调函数（未提供时将清除该手势类型的所有回调）。 |

**示例**

参考[addGlobalGestureListener](#addglobalgesturelistener)接口示例。
