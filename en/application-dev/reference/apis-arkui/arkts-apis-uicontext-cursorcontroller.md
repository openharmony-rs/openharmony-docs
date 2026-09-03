# Class (CursorController)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-08-05T03:04:10.359Z pushedAt=2026-08-06T00:58:08.341Z -->

Provides the capability to set mouse cursor styles, including restoring the default cursor style, setting a system cursor style, and setting a custom cursor style. It is suitable for scenarios where the mouse cursor display effect needs to be dynamically adjusted based on interface interaction states, helping improve the clarity of interface interaction cues.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The APIs of this module can be used only in the stage model.
>
> - To use the following APIs, you must first obtain a CursorController instance by calling [getCursorController()](arkts-apis-uicontext-uicontext.md#getcursorcontroller12) in UIContext, and then call the corresponding methods through this instance.

## restoreDefault<sup>12+</sup>

restoreDefault(): void

Restores the default cursor style.

> **NOTE**
>
> This API does not take effect immediately after being called. Instead, the mouse cursor style is updated in the next frame.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

In this example, the **restoreDefault** API of **CursorController** is used to restore the cursor style when the cursor moves out of the green frame.

```ts
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

![cursor-restoreDefault](figures/cursor-restoreDefault.gif)

## setCursor<sup>12+</sup>

setCursor(value: PointerStyle): void

Sets the cursor style.

**Model restriction:** This API can be used only in the stage model.

> **NOTE**
>
> This API does not take effect immediately. The cursor style will be updated in the next rendering frame.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                      | Mandatory  | Description     |
| ------- | ---------------------------------------- | ---- | ------- |
| value | [PointerStyle](arkts-apis-uicontext-t.md#pointerstyle12) | Yes    | Mouse cursor style. It specifies the system-defined cursor type to set, such as arrow, hand pointer, and crosshair. For details about the meaning of each style, see the PointerStyle enum description. |

**Example**

When the cursor enters the blue box, the cursor style is changed to PointerStyle.WEST through the setCursor method of CursorController.

```ts
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

![cursor-setCursor](figures/cursor-setCursor.gif)

## setCustomCursor

setCustomCursor(value: image.PixelMap, focusX?: number, focusY?: number): void

Sets the custom cursor style.

> **NOTE**
>
> - This API does not take effect immediately after being called. Instead, the mouse cursor style is updated in the next frame.
> - Only static images are supported. Dynamic images are not supported.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                             | Mandatory  | Description                                    |
| ------- | ------------------------------- | ---- | -------------------------------------- |
| value | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes | PixelMap of the custom cursor style. Only static images are supported; dynamic images are not supported. The maximum size is 256 × 256 px. If the image exceeds this size, the setting will not take effect, and the mouse cursor will remain unchanged. |
| focusX | number | No | X coordinate of the custom cursor focus point. The origin is the upper left corner of the cursor image, and the positive direction is to the right. When displayed, this focus point is aligned with the screen coordinates of the system mouse pointer, and all mouse operations such as clicking and dragging are based on this point.<br>Default value: 0<br>Unit: px<br>Value range: [0, image width]. If the value is out of range, the default value is used. |
| focusY | number | No | Y coordinate of the custom cursor focus point. The origin is the upper left corner of the cursor image, and the positive direction is downward. This parameter and **focusX** together determines the point within the image that represents the actual interaction position.<br>Default value: 0<br>Unit: px<br>Value range: [0, image height]. If the value is out of range, the default value is used. |

**Example**

When the cursor enters the blue box and the custom cursor image is loaded, the custom mouse cursor style is set via the [setCustomCursor](#setcustomcursor) API.

```ts
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

![cursor-setCustomCursor](figures/cursor-setCustomCursor.gif)