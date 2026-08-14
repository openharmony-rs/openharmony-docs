# Class (Magnifier)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer:  @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-08-05T03:05:38.456Z pushedAt=2026-08-05T07:14:18.513Z -->

Provides the ability to control the display and hiding of the magnifier. The magnifier enlarges component content to facilitate viewing of details. This is suitable for scenarios where non‑text components (such as images) require detail inspection.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 22.
>
> - For the following APIs, you must first use [getMagnifier()](arkts-apis-uicontext-uicontext.md#getmagnifier22) in **UIContext** to obtain a **Magnifier** instance, and then call the APIs using the obtained instance.
>
> - The magnifier capability of this class does not affect that of text components. For text components, you are advised to use the built-in magnifier capability.

## bind

bind(id: string): void

Binds the magnifier to the component with the specified ID.

> **NOTE**
>
> Before using this API, obtain a **Magnifier** instance through the **getMagnifier()** method in UIContext.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Parameter     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| id | string | Yes   | Component ID, which can be set through the universal attribute [id](./arkui-ts/ts-universal-attributes-component-id.md#id) or [key](./arkui-ts/ts-universal-attributes-component-id.md#key12). If the component ID is an empty string or no component is found based on the specified ID, the magnifier is not displayed.|

**Example**

This example listens to the onTouch event to control the magnifier to zoom in on an image.

```ts
import { Magnifier } from '@kit.ArkUI';

@Entry
@Component
struct MagnifierExample {
  private magnifier: Magnifier = this.getUIContext().getMagnifier();

  build() {
    Column() {
      // Replace $r('app.media.startIcon') with the image resource file you use.
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

![magnifier](figures/magnifier.png)

## show

show(x: number, y: number): void

Sets the position of the component content displayed by the magnifier relative to the upper left corner of the component. After the setting is successful, the magnifier displays the content centered at the coordinate point.

> **NOTE**
>
> - Before using this API, obtain a Magnifier instance through the getMagnifier() method in UIContext.
>
> - Before calling this method, call [bind](#bind) to bind the target component.
>
> - When the content of the component bound to the magnifier changes, the magnifier display content is not automatically updated. You need to actively call the **show** API to update the content.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Parameter     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| x | number | Yes    | Horizontal coordinate of the component content displayed in the magnifier relative to the upper left corner of the component, in vp. The magnifier is not displayed when the coordinate value is greater than the component width or less than 0. If **undefined** is passed, the setting does not take effect and the current display state of the magnifier is retained. |
| y | number | Yes    | Vertical coordinate of the component content displayed in the magnifier relative to the upper left corner of the component, in vp. The magnifier is not displayed when the coordinate value is greater than the component height or less than 0. If **undefined** is passed, the setting does not take effect and the current display state of the magnifier is retained. |

**Example**

For details, see the [bind](#bind) example.

## unbind

unbind(): void

Unbinds the magnifier from the current component. Before using this API, obtain a **Magnifier** instance through the **getMagnifier()** method in UIContext.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

For details, see the [bind](#bind) example.