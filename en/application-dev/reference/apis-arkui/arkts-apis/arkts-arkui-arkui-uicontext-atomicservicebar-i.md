# AtomicServiceBar

```TypeScript
export interface AtomicServiceBar
```

The AtomicServiceBar interface provides the ability to set properties of the atomic service menu bar, including the visibility, background color, title content, title font style, and icon color, and also supports obtaining menu bar layout information and listening for layout changes. It is suitable for scenarios where you need to customize the appearance and behavior of the menu bar in atomic services.

**Since:** 11

<!--Device-unnamed-export interface AtomicServiceBar--><!--Device-unnamed-export interface AtomicServiceBar-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## getBarRect

```TypeScript
getBarRect(): Frame
```

Obtains the layout information of the atomic service menu bar relative to the window. <br>The menu bar position reflected in the layout information already takes its left and right margins into account.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-AtomicServiceBar-getBarRect(): Frame--><!--Device-AtomicServiceBar-getBarRect(): Frame-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [Frame](arkts-arkui-graphics-frame-i.md) | The size and position of bar in vp relative to window. |

**Examples**

```TypeScript
import { AtomicServiceBar, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  build() {
    Button('getBarRect')
      .onClick(() => {
        let uiContext: UIContext = this.getUIContext();
        let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
        if (atomicServiceBar != undefined) {
          let rect = atomicServiceBar.getBarRect();
          hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar Successfully. x:'
            + rect.x + ' y:' + rect.y + ' width:' + rect.width + ' height:' + rect.height);
        } else {
          hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
        }
      })
  }
}
```

## onBarRectChange

```TypeScript
onBarRectChange(callback: Callback<Frame>): void
```

Callback triggered when the size or position of the atomic service menu bar (AtomicServiceMenuBar, the menu capsule in the upper-right corner) changes. It returns the latest layout information of the menu bar. The layout information includes the size and position of the menu bar, with the left and right margins taken into account for the position.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-AtomicServiceBar-onBarRectChange(callback: Callback<Frame>): void--><!--Device-AtomicServiceBar-onBarRectChange(callback: Callback<Frame>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Frame](arkts-arkui-graphics-frame-i.md)&gt; | Yes | Callback used to return the new layout information when the AtomicServiceMenuBar layout changes. |

**Examples**

## setBackgroundColor

```TypeScript
setBackgroundColor(color: Nullable< Color | number | string>): void
```

Sets the background color of the atomic service menu bar. <br>Since API version 12, the background of the atomic service menu bar is hidden by default. <br>When setBackgroundColor() is called in atomic services, the color parameter is ignored, and the background <br>color of the menu bar cannot be set.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AtomicServiceBar-setBackgroundColor(color: Nullable< Color | number | string>): void--><!--Device-AtomicServiceBar-setBackgroundColor(color: Nullable< Color | number | string>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Nullable](arkts-arkui-nullable-t.md)&lt;[Color](arkts-arkui-color-e.md) &#124; number &#124; string&gt; | Yes | Color of the atomic service menu bar. The value undefined means to use the default color. A number value indicates a HEX color in RGB or ARGB format, for example, 0xffffff. A string value indicates a color in RGB or ARGB format, for example, '#ffffff'. Since API version 12, this parameter will be ignored in atomic services. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err) {
        hilog.info(0x0000, 'testTag', 'LoadContent failed.');
        return;
      }
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar Successfully.');
        atomicServiceBar.setBackgroundColor(0x88888888);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

## setIconColor

```TypeScript
setIconColor(color: Nullable< Color | number | string>): void
```

Sets the color of the atomic service menu bar icon. <br>Since API version 12, the atomic service menu bar is hidden by default and replaced with a floating button. <br>When setIconColor() is called in atomic services, the color parameter is ignored, and the menu bar icon color <br>cannot be set.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AtomicServiceBar-setIconColor(color: Nullable< Color | number | string>): void--><!--Device-AtomicServiceBar-setIconColor(color: Nullable< Color | number | string>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Nullable](arkts-arkui-nullable-t.md)&lt;[Color](arkts-arkui-color-e.md) &#124; number &#124; string&gt; | Yes | Color of the atomic service menu bar. The value undefined means to use the default color. A number value indicates a HEX color in RGB or ARGB format, for example, 0xffffff. A string value indicates a color in RGB or ARGB format, for example, '#ffffff'. Since API version 12, this parameter will be ignored in atomic services. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err) {
        hilog.info(0x0000, 'testTag', 'LoadContent failed.');
        return;
      }
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar Successfully.');
        atomicServiceBar.setIconColor(0x12345678);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

## setTitleContent

```TypeScript
setTitleContent(content: string): void
```

Sets the title content of the atomic service menu bar. <br>Since API version 12, the title of the atomic service menu bar is hidden by default. <br>When setTitleContent() is called in atomic services, the content parameter is ignored, and the menu bar title <br>cannot be set.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AtomicServiceBar-setTitleContent(content: string): void--><!--Device-AtomicServiceBar-setTitleContent(content: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | string | Yes | Title content of the atomic service menu bar. Since API version 12, this parameter will be ignored in atomic services. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err) {
        hilog.info(0x0000, 'testTag', 'LoadContent failed.');
        return;
      }
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar Successfully.');
        atomicServiceBar.setTitleContent('text2');
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

## setTitleFontStyle

```TypeScript
setTitleFontStyle(font: FontStyle): void
```

Sets the font style of the atomic service menu bar title. <br>Since API version 12, the title of the atomic service menu bar is hidden by default. <br>When setTitleFontStyle() is called in atomic services, the font parameter is ignored, and the font style of <br>the menu bar title, such as italic, cannot be set.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AtomicServiceBar-setTitleFontStyle(font: FontStyle): void--><!--Device-AtomicServiceBar-setTitleFontStyle(font: FontStyle): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| font | [FontStyle](arkts-arkui-fontstyle-e.md) | Yes | Font style of the atomic service menu bar title. Since API version 12, this parameter will be ignored in atomic services. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err) {
        hilog.info(0x0000, 'testTag', 'LoadContent failed.');
        return;
      }
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar Successfully.');
        atomicServiceBar.setTitleFontStyle(FontStyle.Normal);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

## setVisible

```TypeScript
setVisible(visible: boolean): void
```

Sets whether the atomic service menu bar is visible. <br>Since API version 12, the atomic service menu bar is hidden by default and replaced with a floating button. <br>When setVisible() is called in atomic services, the visible parameter is ignored, and menu bar cannot be <br>displayed or hidden.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AtomicServiceBar-setVisible(visible: boolean): void--><!--Device-AtomicServiceBar-setVisible(visible: boolean): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visible | boolean | Yes | Whether the atomic service menu bar is visible. The value true means the atomic service menu bar is visible, and false means the opposite. Since API version 12, this parameter will be ignored in atomic services. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err) {
        hilog.info(0x0000, 'testTag', 'LoadContent failed.');
        return;
      }
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar Successfully.');
        atomicServiceBar.setVisible(false);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```
