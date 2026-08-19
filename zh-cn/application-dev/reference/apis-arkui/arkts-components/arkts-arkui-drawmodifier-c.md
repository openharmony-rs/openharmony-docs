# DrawModifier

Defined the draw modifier of node. Provides draw callbacks for the associated Node.

**起始版本：** 12

<!--Device-unnamed-declare class DrawModifier--><!--Device-unnamed-declare class DrawModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## drawBehind

```TypeScript
drawBehind?(drawContext: DrawContext): void
```

drawBehind Method. Executed before drawing associated Node.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawBehind?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawBehind?(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-drawcontext-t.md) | 是 | The drawContext used to draw. |

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

## drawContent

```TypeScript
drawContent?(drawContext: DrawContext): void
```

drawContent Method. Executed when associated Node is drawing, the default drawContent method will be replaced if this method is set.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawContent?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawContent?(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-drawcontext-t.md) | 是 | The drawContext used to draw. |

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

## drawForeground

```TypeScript
drawForeground(drawContext: DrawContext): void
```

前景绘制，在关联节点和其子节点绘制后执行

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void--><!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-drawcontext-t.md) | 是 | 用来绘制的drawContext |

**示例**

请参考[示例2（通过DrawModifier对容器的前景进行自定义绘制）](#示例2通过drawmodifier对容器的前景进行自定义绘制)。

## drawFront

```TypeScript
drawFront?(drawContext: DrawContext): void
```

drawFront Method. Executed after drawing associated Node.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawFront?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawFront?(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-drawcontext-t.md) | 是 | The drawContext used to draw. |

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

## drawOverlay

```TypeScript
drawOverlay(drawContext: DrawContext): void
```

在关联的Node及其所有子节点绘制完成后，在悬浮层中绘制内容。 自定义绘制包含五个层级：内容背景层、内容层、内容前景层、前景层和悬浮层。 - 前景层和悬浮层在子节点之后绘制。 - 悬浮层与前景层的区别在于：悬浮层可以在组件的边界范围外进行绘制。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void--><!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-drawcontext-t.md) | 是 | 用于绘制的drawContext |

**示例**

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

  // 重载drawOverlay方法，实现自定义绘制遮罩层
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
  // 将自定义绘制遮罩层的类实例化，传入UIContext实例
  private overlayModifier: MyOverlayDrawModifier = new MyOverlayDrawModifier(this.getUIContext());

  build() {
    Column() {
      Text('此文本是子节点')
        .fontSize(36)
        .width('100%')
        .height('100%')
        .textAlign(TextAlign.Center)
    }
    .margin(50)
    .width(280)
    .height(300)
    .backgroundColor(0x87CEEB)
    // 调用此接口并传入自定义绘制遮罩层的类实例，即可实现自定义绘制遮罩层
    .drawModifier(this.overlayModifier)
  }
}
```

## invalidate

```TypeScript
invalidate(): void
```

Invalidate the component, which will cause a re-render of the component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-invalidate(): void--><!--Device-DrawModifier-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

