# CursorController

```TypeScript
export class CursorController
```

Provides the capability to set cursor styles.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - In the following API examples, you must first use [getCursorController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcursorcontroller) in
> **UIContext** to obtain a **CursorController** instance, and then call the APIs using the obtained instance.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## restoreDefault

```TypeScript
restoreDefault(): void
```

Restores the default cursor style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

In this example, the restoreDefault API of CursorController is used to restore the cursor style when the cursor moves out of the green frame.

```TypeScript
import { pointer } from '@kit.InputKit';
import { CursorController } from '@kit.ArkUI';

@Entry
@Component
struct CursorControlExample {
  cursorController: CursorController = this.getUIContext().getCursorController();

  build() {
    Column() {
      Row().height(200).width(200).backgroundColor(Color.Green).position({x: 150, y:70})
        .onHover((isHover) => {
          if (isHover) {
            this.cursorController.setCursor(pointer.PointerStyle.EAST);
          } else {
            console.info('restoreDefault');
            this.cursorController.restoreDefault();
          }
        })
    }.width('100%')
  }
}
```

## setCursor

```TypeScript
setCursor(value: PointerStyle): void
```

Sets the cursor style.

> **NOTE:** 
> 
> This API does not take effect immediately. The cursor style will be updated in the next rendering frame.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PointerStyle](arkts-arkui-pointerstyle-t.md) | Yes | Pointer style. |

**Examples**

When the cursor enters the blue box, the cursor style is changed to PointerStyle.WEST through the setCursor method of CursorController.

```TypeScript
import { pointer } from '@kit.InputKit';
import { CursorController } from '@kit.ArkUI';

@Entry
@Component
struct CursorControlExample {
  cursorCustom: CursorController = this.getUIContext().getCursorController();

  build() {
    Column() {
      Row().height(200).width(200).backgroundColor(Color.Blue).position({x: 100, y:70})
        .onHover((isHover) => {
          if (isHover) {
            this.cursorCustom.setCursor(pointer.PointerStyle.WEST);
          } else {
            this.cursorCustom.restoreDefault();
          }
        })
    }.width('100%')
  }
}
```

## setCustomCursor

```TypeScript
setCustomCursor(value: image.PixelMap, focusX?: number, focusY?: number): void
```

Sets the custom cursor style.

> **NOTE:** 
> 
> This API does not take effect immediately. The cursor style will be updated in the next rendering frame.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Pixel map of the custom mouse cursor style. |
| focusX | number | No | X coordinate of the custom cursor's hotspot. The hotspot refers to the actual location where the click occurs.<br>Default value: **0**<br>Unit: px<br>Value range: [0, +∞) |
| focusY | number | No | Y coordinate of the custom cursor's hotspot.<br>Default value: **0**<br>Unit: px<br>Value range: [0, +∞) |

**Examples**

When the cursor enters the blue box and the custom cursor image is loaded, the custom mouse cursor style is set via the [setCustomCursor](#setcustomcursor) API.

```TypeScript
import { image } from '@kit.ImageKit';
import { CursorController } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CustomCursorExample {
  cursorController: CursorController = this.getUIContext().getCursorController();
  @State pixelMap: image.PixelMap | undefined = undefined;

  async loadPixelMapFromRawFile(): Promise<void> {
    try {
      // 1. Obtain the resource manager and add a null check.
      const uiContext = this.getUIContext();
      if (!uiContext) {
        console.error('UIContext is undefined');
        return;
      }
      const context = uiContext.getHostContext();
      if (!context) {
        console.error('HostContext is undefined');
        return;
      }
      const resourceManager = context.resourceManager;
      if (!resourceManager) {
        console.error('ResourceManager is undefined');
        return;
      }
      // 2. Read the image file in rawfile.
      const fileData: Uint8Array = await resourceManager.getRawFileContent('cursor.png');
      const buffer = fileData.buffer.slice(0);
      // 3. Create an ImageSource.
      const imageSource = image.createImageSource(buffer);
      // 4. Create a PixelMap (you can specify the desired size).
      const pixelMap = await imageSource.createPixelMap({
        desiredSize: { width: 32, height: 32 }
      });
      this.pixelMap = pixelMap;
      console.info('Custom cursor loaded successfully');
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to load cursor. Code: ${err.code}, message: ${err.message}`);
    }
  }

  build() {
    Column() {
      Button('load image')
        .width('40%')
        .height('7%')
        .fontSize('30vp')
        .margin(70)
        .backgroundColor(Color.Blue)
        .onClick(() => {
          // Tap the button to load the PixelMap.
          this.loadPixelMapFromRawFile();
        })
      Row()
        .height(200)
        .width(200)
        .backgroundColor(Color.Blue)
        .onHover((isHover: boolean) => {
          if (isHover && this.pixelMap != undefined) {
            // Set the custom cursor style, with the focus position set to (16, 16), that is, the cursor center.
            this.cursorController.setCustomCursor(this.pixelMap, 16, 16);
          } else {
            this.cursorController.restoreDefault();
          }
        })
    }
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
    .width('100%')
    .height('100%')
  }

  aboutToDisappear(): void {
    // Release the PixelMap resource.
    if (this.pixelMap) {
      this.pixelMap.release();
      this.pixelMap = undefined;
    }
    this.cursorController.restoreDefault();
  }
}
```
