# ResolvedUIContext

ResolvedUIContext实例对象。

> **说明：**  
>  
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。  
>  
> - ResolvedUIContext继承自[UIContext](arkts-arkui-uicontext.md)，该类对象包含[UIContext](arkts-arkui-uicontext.md)实例和  
> [UIContext](arkts-arkui-uicontext.md)的解析策略。

**继承/实现关系：** ResolvedUIContext extends [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**起始版本：** 22

<!--Device-unnamed-export class ResolvedUIContext extends UIContext--><!--Device-unnamed-export class ResolvedUIContext extends UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## strategy

```TypeScript
strategy: ResolveStrategy
```

[UIContext](arkts-arkui-uicontext.md)的解析策略。

**类型：** ResolveStrategy

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ResolvedUIContext-strategy: ResolveStrategy--><!--Device-ResolvedUIContext-strategy: ResolveStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

