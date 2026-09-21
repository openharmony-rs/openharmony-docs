# DrawModifier

```TypeScript
declare class DrawModifier
```

Defined the draw modifier of node. Provides draw callbacks for the associated Node. Each DrawModifier instance can be set for only one component. Repeated setting is not allowed.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## drawBehind

```TypeScript
drawBehind?(drawContext: DrawContext): void
```

drawBehind Method. Executed before drawing associated Node.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | The drawContext used to draw. |

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).

## drawContent

```TypeScript
drawContent?(drawContext: DrawContext): void
```

drawContent Method. Executed when associated Node is drawing, the default drawContent method will be replaced if this method is set.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | The drawContext used to draw. |

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).

## drawForeground

```TypeScript
drawForeground(drawContext: DrawContext): void
```

drawforeground Method. This method is executed after drawing the associated Node and its children. It allows you to perform additional drawing operations on top of the already rendered content. This can be useful for adding visual elements that should appear above the main content.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | The drawContext used to draw. |

**Examples**

See [Example 2: Implementing Custom Foreground Drawing for a Container Through DrawModifier](#example-2-implementing-custom-foreground-drawing-for-a-container-through-drawmodifier).

## drawFront

```TypeScript
drawFront?(drawContext: DrawContext): void
```

drawFront Method. Executed after drawing associated Node.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | The drawContext used to draw. |

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).

## drawOverlay

```TypeScript
drawOverlay(drawContext: DrawContext): void
```

Draws content in the overlay layer after the associated Node and all its children have been drawn.

Custom drawing consists of five layers: Behind, Content, Front, Foreground, and Overlay.

- The Foreground and Overlay layers are drawn after child nodes.  
- The Overlay layer differs from Foreground in that it can draw outside the bounds of the component.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | Yes | The drawContext used to draw |

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

Invalidate the component, which will cause a re-render of the component. No overloading is allowed or needed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

See [Example 1: Implementing Custom Drawing Through DrawModifier](#example-1-implementing-custom-drawing-through-drawmodifier).
