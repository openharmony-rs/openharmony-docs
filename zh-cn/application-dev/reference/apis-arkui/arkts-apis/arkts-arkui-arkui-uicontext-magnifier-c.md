# Magnifier

提供控制放大镜的显示与隐藏的能力，放大镜会对组件内容进行放大显示，便于查看组件细节。适用于非文本类组件（如图片）需要查看细节的场景。

> **说明：**
> 
> - 以下API需先使用UIContext中的[getMagnifier()](arkts-arkui-arkui-uicontext-uicontext-c.md#getmagnifier)方法获取Magnifier实例，再通过此实例调用对应方法。
> 
> - 与文本类组件自带的放大镜能力互不影响，文本类组件推荐使用自带的放大镜能力。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## bind

```TypeScript
bind(id: string): void
```

绑定放大镜与指定id的组件。

> **说明：**
> 
> 使用前需先通过UIContext中的getMagnifier()方法获取Magnifier实例。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件id，可通过通用属性id或key设置。当组件id为空字符串或未找到匹配id的组件时，不显示放大镜。 |

**示例**

该示例通过监听onTouch事件控制放大镜对图片进行放大显示。

```TypeScript
import { Magnifier } from '@kit.ArkUI';

@Entry
@Component
struct MagnifierExample {
  private magnifier: Magnifier = this.getUIContext().getMagnifier();

  build() {
    Column() {
      // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.startIcon'))
        .draggable(false)
        .width(200)
        .height(200)
        .margin(50)
        .id('image')
        .onTouch((event: TouchEvent) => {
          if (event && event.sourceTool === SourceTool.Finger) {
            if (event.type === TouchType.Down) {
              this.magnifier.bind('image');
            } else if (event.type === TouchType.Move) {
              let touchX = event.touches[0].x;
              let touchY = event.touches[0].y;
              this.magnifier.show(touchX, touchY);
            } else if (event.type === TouchType.Up) {
              this.magnifier.unbind();
            } else if (event.type === TouchType.Cancel) {
              this.magnifier.unbind();
            }
          }
        })
    }
  }
}
```

## show

```TypeScript
show(x: number, y: number): void
```

设置放大镜显示的组件内容相对于组件左上角的位置，设置成功后放大镜会对以该坐标点为中心的区域内容进行放大显示。

> **说明：**
> 
> - 使用前需先通过UIContext中的getMagnifier()方法获取Magnifier实例。
> 
> - 调用此方法前，需先调用[bind](#bind)方法绑定目标组件。
> 
> - 当与放大镜绑定的组件自身内容发生变化时，放大镜显示内容不会自动更新，需要主动调用show接口对放大镜显示内容进行更新。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 放大镜显示的组件内容相对于组件左上角的水平方向坐标，单位为vp。当坐标值大于组件宽度或小于0时不显示放大镜；传入undefined时不生效，保持放大镜当前的显示状态。 |
| y | number | 是 | 放大镜显示的组件内容相对于组件左上角的垂直方向坐标，单位为vp。当坐标值大于组件高度或小于0时不显示放大镜；传入undefined时不生效，保持放大镜当前的显示状态。 |

**示例**

请参考[bind](#bind)示例。

## unbind

```TypeScript
unbind(): void
```

解除放大镜与当前组件的绑定。使用前需先通过UIContext中的getMagnifier()方法获取Magnifier实例。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考[bind](#bind)示例。
