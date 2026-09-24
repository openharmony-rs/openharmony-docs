# UIInspector

```TypeScript
export class UIInspector
```

class UIInspector

提供注册组件布局和组件绘制送显完成回调通知的能力。送显指节点的绘制命令发送到图形服务并完成显示。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作，适用于需要精确感知组件布局和绘制时机的场景。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## createComponentObserver

```TypeScript
createComponentObserver(id: string): inspector.ComponentObserver
```

注册组件布局和组件绘制送显完成回调通知。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 指定组件id，该id通过通用属性id或者key设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [inspector.ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | 组件回调事件监听句柄，用于注册和取消注册监听回调。 |

**示例**

```TypeScript
import { inspector, UIInspector } from '@kit.ArkUI';

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text('UIInspector')
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80)
      }.width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener: inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      console.info('TEXT_ID layout complete');
    }
    let onDrawComplete: () => void = (): void => {
      console.info('TEXT_ID draw complete');
    }

    this.listener.on('layout', onLayoutComplete);
    this.listener.on('draw', onDrawComplete);

    // 通过句柄取消注册对应组件的监听回调，由开发者自行决定在何时调用。
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```

<a id="createcomponentobserver-1"></a>

## createComponentObserver

```TypeScript
createComponentObserver(id: string | number): inspector.ComponentObserver
```

注册组件布局和组件绘制送显完成回调通知。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string &#124; number | 是 | 指定组件id，该id通过通用属性id或者key设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [inspector.ComponentObserver](arkts-arkui-inspector-componentobserver-i.md) | 组件回调事件监听句柄，用于注册和取消注册监听回调。 |

**示例**

```TypeScript
import { inspector, UIInspector } from '@kit.ArkUI';

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text('UIInspector')
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80)
      }.width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener: inspector.ComponentObserver = this.uiInspector.createComponentObserver('TEXT_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      console.info('TEXT_ID layout complete');
    }
    let onDrawComplete: () => void = (): void => {
      console.info('TEXT_ID draw complete');
    }
    let onLayoutChildrenComplete: () => void = (): void => {
      console.info('UIInspectorExample children layout');
    }

    this.listener.on('layout', onLayoutComplete);
    this.listener.on('draw', onDrawComplete);

    let listenerForThis = this.getUIContext().getUIInspector().createComponentObserver(this.getUniqueId());
    listenerForThis.onLayoutChildren(onLayoutChildrenComplete);

    // 通过句柄取消注册对应组件的监听回调，由开发者自行决定在何时调用。
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
    // listenerForThis.offLayoutChildren(onLayoutChildrenComplete)
  }
}
```
