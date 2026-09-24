# ComponentUtils

```TypeScript
export class ComponentUtils
```

提供获取组件绘制区域坐标、大小、平移、缩放、旋转及仿射矩阵等属性信息的能力，适用于需要查询组件绘制区域信息的场景，帮助开发者获取组件布局结果。

> **说明：** 
> 
> - 本Class首批接口从API version 10开始支持。
> 
> - 以下API需先使用UIContext中的[getComponentUtils()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentutils)方法获取到ComponentUtils对象，再通过该对象调用对应方法。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## getRectangleById

```TypeScript
getRectangleById(id: string): componentUtils.ComponentInfo
```

获取组件大小、位置、平移、缩放、旋转及仿射矩阵属性信息。

> **说明：** 
> 
> 该接口需要在目标组件布局完成以后获取目标组件区域大小信息，建议在[布局回调](arkts-arkui-arkui-inspector.md)中使用该接口。如果组件动态创建但未挂载组件树，则无法通过该接口获取正常的
> 组件信息。因为此时组件一般未经过UI框架的测量与布局，请确保组件已挂载到组件树后再尝试获取组件信息。
> 
> 该接口返回的组件位置为布局位置，某些属性计算不支持，如位置设置类[offset](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#offset)、[markAnchor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#markanchor)、[Edges](arkts-arkui-graphics-edges-i.md) 和[LocalizedEdges](arkts-arkui-localizededges-i.md)类型的[position](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#position)，以及图形变换类[rotate](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#rotate)、[translate](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#translate)、[scale](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#scale)、[transform](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#transform)。可使用替代接口[getPositionToWindowWithTransform](arkts-arkui-framenode-c.md#getpositiontowindowwithtransform)，获取组件相对于窗口且带有绘制属性的位置偏移。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件唯一标识id，需确保该id对应的组件已挂载到组件树且完成布局。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [componentUtils.ComponentInfo](arkts-arkui-componentutils-componentinfo-i.md) | 组件大小、位置、平移、缩放、旋转及仿射矩阵属性信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | UI execution context not found. |

**示例**

```TypeScript
import { ComponentUtils } from '@kit.ArkUI';

@Entry
@Component
struct Index {
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
          this.message = 'Welcome';
          let componentUtils: ComponentUtils = this.getUIContext().getComponentUtils();
          let componentInfo = componentUtils.getRectangleById("HelloWorld");
          let width = componentInfo.size.width; // 获取组件的宽度
          let height = componentInfo.size.height; // 获取组件的高度
          let localOffsetX = componentInfo.localOffset.x; // 获取组件相对于父组件的x轴偏移
          let localOffsetY = componentInfo.localOffset.y; // 获取组件相对于父组件的y轴偏移
          console.info(`width: ${width}, height: ${height}, localOffsetX: ${localOffsetX}, localOffsetY: ${localOffsetY}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
