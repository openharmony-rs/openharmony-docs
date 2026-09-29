# DrawModifier

```TypeScript
declare class DrawModifier
```

DrawModifier can set the drawing methods of the mask layer (drawOverlay&lt;sup&gt;23+&lt;/sup&gt;), foreground (drawForeground&lt;sup&gt;20+&lt;/sup&gt;), content foreground (drawFront), content (drawContent), and content background (drawBehind), and also provides the [invalidate](#invalidate) method to actively trigger redrawing. Each DrawModifier instance can be set to only one component, and repeated setting is prohibited.

> **NOTE:** 
> 
> The drawing order from bottom to top is: content background (drawBehind) → content (drawContent) → content
> foreground (drawFront) → foreground (drawForeground) → mask layer (drawOverlay). Each layer is drawn
> independently, and the methods of each layer are optional to implement.

**Since:** 12

<!--Device-unnamed-declare class DrawModifier--><!--Device-unnamed-declare class DrawModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## drawBehind

```TypeScript
drawBehind?(drawContext: DrawContext): void
```

Draws the content background. Override this method to implement custom content background drawing. The background is located below the component content layer, and is suitable for scenarios where decorative background elements need to be added at the bottom layer of the component. The Canvas in the [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) of this API is a temporary canvas used to record instructions, not the actual canvas of the node. For usage, see [Adjusting the Transformation Matrix of the Custom Drawing Canvas](../../../ui/arkts-user-defined-extension-drawModifier.md#adjusting-the-transformation-matrix-of-the-custom-drawing-canvas).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawModifier-drawBehind?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawBehind?(drawContext: DrawContext): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | Graphics drawing context that provides properties such as canvas (canvas object) and size (drawing area size), used to perform specific drawing operations in custom drawing methods. |

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).

## drawContent

```TypeScript
drawContent?(drawContext: DrawContext): void
```

Draws the content. Override this method to implement custom content drawing, which will replace the component's default content drawing function. It is suitable for scenarios where the component content drawing needs to be fully customized and the component's original content drawing logic is not used. The Canvas in the [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) of this API is a temporary canvas used to record instructions, not the actual canvas of the node. For usage, see [Adjusting the Transformation Matrix of the Custom Drawing Canvas](../../../ui/arkts-user-defined-extension-drawModifier.md#adjusting-the-transformation-matrix-of-the-custom-drawing-canvas).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawModifier-drawContent?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawContent?(drawContext: DrawContext): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | Graphics drawing context that provides properties such as canvas (canvas object) and size (drawing area size), used to perform specific drawing operations in custom drawing methods. |

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).

## drawForeground

```TypeScript
drawForeground(drawContext: DrawContext): void
```

Draws the foreground. Override this method to implement custom foreground drawing. Compared with [drawFront](#drawfront) (content foreground), drawForeground is at a higher layer and is drawn above the content foreground and below the mask layer. drawFront is suitable for drawing the foreground effect of the component content itself, while drawForeground is suitable for scenarios where an additional foreground effect needs to be added above the content foreground. The Canvas in the [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) of this API is a temporary canvas used to record instructions, not the actual canvas of the node. For usage, see [Adjusting the Transformation Matrix of the Custom Drawing Canvas](../../../ui/arkts-user-defined-extension-drawModifier.md#adjusting-the-transformation-matrix-of-the-custom-drawing-canvas).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void--><!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | Graphics drawing context that provides properties such as canvas (canvas object) and size (drawing area size), used to perform specific drawing operations in custom drawing methods. |

**Examples**

See [Example 2: Implementing Custom Foreground Drawing for a Container Through DrawModifier](#example-2-implementing-custom-foreground-drawing-for-a-container-through-drawmodifier).

## drawFront

```TypeScript
drawFront?(drawContext: DrawContext): void
```

Draws the content foreground. Override this method to implement custom content foreground drawing. The content foreground is located between the content and the foreground, and is suitable for scenarios where drawing content needs to be added above the component content and below the component foreground. The Canvas in the [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) of this API is a temporary canvas used to record instructions, not the actual canvas of the node. For usage, see [Adjusting the Transformation Matrix of the Custom Drawing Canvas](../../../ui/arkts-user-defined-extension-drawModifier.md#adjusting-the-transformation-matrix-of-the-custom-drawing-canvas).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawModifier-drawFront?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawFront?(drawContext: DrawContext): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | Graphics drawing context that provides properties such as canvas (canvas object) and size (drawing area size), used to perform specific drawing operations in custom drawing methods. |

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).

## drawOverlay

```TypeScript
drawOverlay(drawContext: DrawContext): void
```

Interface for custom drawing of the mask. If this method is overridden, custom drawing of the mask can be performed. The mask is the topmost drawing layer, suitable for scenarios where a mask effect (such as highlighting or masking) needs to be added to the topmost layer of a component. The Canvas in [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) of this interface is a temporary canvas used to record instructions, not the actual canvas of the node. For usage, see [Adjusting the Transformation Matrix of the Custom Drawing Canvas](../../../ui/arkts-user-defined-extension-drawModifier.md#adjusting-the-transformation-matrix-of-the-custom-drawing-canvas).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void--><!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | Graphics drawing context that provides properties such as canvas (canvas object) and size (drawing area size), used to perform specific drawing operations in custom drawing methods. |

**Examples**

```TypeScript
// test.ets
import { drawing } from '@kit.ArkGraphics2D';

class MyOverlayDrawModifier extends DrawModifier {
  public scaleX: number = 3;
  public scaleY: number = 3;
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    super();
    this.uiContext = uiContext;
  }

  // Override the drawOverlay method to implement custom drawing of the overlay layer.
  drawOverlay(context: DrawContext): void {
    const brush = new drawing.Brush();
    brush.setColor({
      alpha: 255,
      red: 0,
      green: 50,
      blue: 100
    });
    context.canvas.attachBrush(brush);
    const halfWidth = context.size.width / 2;
    const halfHeight = context.size.height / 2;
    context.canvas.drawRect({
      left: this.uiContext.vp2px(halfWidth - 30 * this.scaleX),
      top: this.uiContext.vp2px(halfHeight - 30 * this.scaleY),
      right: this.uiContext.vp2px(halfWidth + 30 * this.scaleX),
      bottom: this.uiContext.vp2px(halfHeight + 60 * this.scaleY)
    });
  }
}

@Entry
@Component
struct DrawModifierExample {
  // Instantiate the class for the custom drawing overlay layer and pass in the UIContext instance.
  private overlayModifier: MyOverlayDrawModifier = new MyOverlayDrawModifier(this.getUIContext());

  build() {
    Column() {
      Text('Here is a child node')
        .fontSize(36)
        .width('100%')
        .height('100%')
        .textAlign(TextAlign.Center)
    }
    .margin(50)
    .width(280)
    .height(300)
    .backgroundColor(0x87CEEB)
    // Call this API and pass in the class instance of the custom drawing overlay layer to implement the custom drawing overlay layer.
    .drawModifier(this.overlayModifier)
  }
}
```

## invalidate

```TypeScript
invalidate(): void
```

Interface for proactively triggering redrawing. Developers do not need to and cannot override this method. Calling it triggers redrawing of the bound component. When the attributes that custom drawing depends on (such as size, color, and position) change, for example, when drawing parameters are dynamically updated during an animation, call this method to make the latest drawing effect take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawModifier-invalidate(): void--><!--Device-DrawModifier-invalidate(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).
