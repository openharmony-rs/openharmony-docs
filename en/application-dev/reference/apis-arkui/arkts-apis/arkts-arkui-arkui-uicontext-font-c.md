# Font

Provides APIs for registering custom fonts.

> **NOTE:** 
> 
> - In the following API examples, you must first use [getFont()](arkts-arkui-arkui-uicontext-uicontext-c.md#getfont) in **UIContext** to obtain a **Font** instance, and then call the APIs using the obtained instance.
> 
> - You are advised to use the [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) API of the font engine to register custom fonts.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## getFontByName

```TypeScript
getFontByName(fontName: string): font.FontInfo
```

Obtains information about a system font based on the font name.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontName | string | Yes | System font name. |

**Return value:**

| Type | Description |
| --- | --- |
| [font.FontInfo](arkts-arkui-font-fontinfo-i.md) | Detailed information of the font.<br>If no font is found, **undefined** is returned. |

## getSystemFontList

```TypeScript
getSystemFontList(): Array<string>
```

Obtains the list of supported fonts.

This API only takes effect on PCs/2-in-1 devices and returns an empty array on other devices.

You are advised to use the [getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md) API to obtain the latest system-supported font list data.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of supported fonts. |

## registerFont

```TypeScript
registerFont(options: font.FontOptions): void
```

Registers a custom font with the font manager.

This API is asynchronous and does not support concurrent calls.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [font.FontOptions](arkts-arkui-font-fontoptions-i.md) | Yes | Information about the custom font to register.<br>**NOTE:** <br>When setting the path to the font file, you are advised to use a string with the **file://** path prefix for resources within the system sandbox path. Ensure that the file exists in the sandbox directory path and has read permissions. |
