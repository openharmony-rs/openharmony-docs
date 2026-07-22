# ComponentUtils

提供获取组件绘制区域坐标和大小的能力。
> **说明：**  
>  
> - 本Class首批接口从API version 10开始支持。  
>  
> - 以下API需先使用UIContext中的[getComponentUtils()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentutils)方法获取到ComponentUtils对象，再通过该对象调用对应方法。

**起始版本：** 10

<!--Device-unnamed-export class ComponentUtils--><!--Device-unnamed-export class ComponentUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## getRectangleById

```TypeScript
getRectangleById(id: string): componentUtils.ComponentInfo
```

获取组件大小、位置、平移、缩放、旋转及仿射矩阵属性信息。
> **说明：**  
>  
> 该接口需要在目标组件布局完成以后获取目标组件区域大小信息，建议在[布局回调](arkts-arkui-inspector.md)中使用该接口。如果组件动态创建但未挂载组件树，则无法通过该接口获取正常的  
> 组件信息。因为组件在未挂载组件树的情况下，一般未经过UI框架正常的测量与布局，此时请确保组件正常挂载组件树后再尝试获取组件信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentUtils-getRectangleById(id: string): componentUtils.ComponentInfo--><!--Device-ComponentUtils-getRectangleById(id: string): componentUtils.ComponentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件唯一标识id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| componentUtils.ComponentInfo | Size, position, translation, scaling, rotation, and affine matrix information of the component. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | UI execution context not found. |

