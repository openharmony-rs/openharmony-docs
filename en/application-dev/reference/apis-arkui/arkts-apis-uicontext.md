# Module Description
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

In the stage model, WindowStage or Window can load pages and create UI instances through the [loadContent](arkts-apis-window-Window.md#loadcontent9) API, and then render the page content to the associated windows. Therefore, a UI instance is bound to a window on a one-to-one basis. Global UI APIs associated with a specific UI instance execution context trace the UI context through the call chain when called. If such APIs are called in a non-UI page or in an asynchronous callback not bound to the current UI context, the UI context may not be traceable, causing the API to fail. This module provides UIContext and its related capabilities to obtain and operate the context of a specified UI instance, such as displaying dialog, performing page routing, querying component information, querying media, and perform focus control and drag control. It also allows you to execute tasks within a specified UIContext scope via [runScopedTask](arkts-apis-uicontext-uicontext.md#runscopedtask), preventing API failures caused by unclear UI context.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

## Modules to Import

```ts
import {
  AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager,
  PromptAction, Router, UIContext, ResolvedUIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MeasureUtils, FrameCallback,
  OverlayManagerOptions, TargetInfo, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, Magnifier
} from '@kit.ArkUI';
```

**System capability:** SystemCapability.ArkUI.ArkUI.Full
