# DrawModifier

```TypeScript
declare class DrawModifier
```

DrawModifier可设置遮罩层（drawOverlay&lt;sup&gt;23+&lt;/sup&gt;）、前景（drawForeground&lt;sup&gt;20+&lt;/sup&gt;）、内容前景（drawFront）、内容（drawContent）和内容背景（drawBehind）的绘制方法，还提供主动触发重绘的方法[invalidate](#invalidate)。每个DrawModifier实例只能设置到一个组件上，禁止重复设置。  
> **说明：** 
> 
> 绘制顺序从下到上依次为：内容背景（drawBehind）→ 内容（drawContent）→ 内容前景（drawFront）→ 前景（drawForeground）→ 遮罩层（drawOverlay）。
> 每个层级独立绘制，各层级方法可选实现。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## drawBehind

```TypeScript
drawBehind?(drawContext: DrawContext): void
```

自定义绘制内容背景的接口，若重载该方法则可进行内容背景的自定义绘制。背景位于组件内容层之下，适用于需要在组件底层添加装饰性背景元素的场景。该接口的DrawContext中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-extension-drawModifier.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | 是 | 图形绘制上下文，提供canvas（画布对象）和size（绘制区域尺寸）等属性，用于在自定义绘制方法中执行具体的绘制操作。 |

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

## drawContent

```TypeScript
drawContent?(drawContext: DrawContext): void
```

自定义绘制内容的接口，若重载该方法则可进行内容的自定义绘制，会替换组件原本的内容绘制函数。适用于需要完全自定义组件内容绘制、不使用组件原本内容绘制逻辑的场景。该接口的DrawContext中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-extension-drawModifier.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | 是 | 图形绘制上下文，提供canvas（画布对象）和size（绘制区域尺寸）等属性，用于在自定义绘制方法中执行具体的绘制操作。 |

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

## drawForeground

```TypeScript
drawForeground(drawContext: DrawContext): void
```

自定义绘制前景的接口，若重载该方法则可进行前景的自定义绘制。与[drawFront](#drawfront)（内容前景）相比，drawForeground位于更高层级，绘制在内容前景之上、遮罩层之下。drawFront适用于绘制组件内容自身的前景效果，drawForeground适用于需要在内容前景之上添加额外前景效果的场景。该接口的DrawContext中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-extension-drawModifier.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | 是 | 图形绘制上下文，提供canvas（画布对象）和size（绘制区域尺寸）等属性，用于在自定义绘制方法中执行具体的绘制操作。 |

**示例**

请参考[示例2（通过DrawModifier对容器的前景进行自定义绘制）](#示例2通过drawmodifier对容器的前景进行自定义绘制)。

## drawFront

```TypeScript
drawFront?(drawContext: DrawContext): void
```

自定义绘制内容前景的接口，若重载该方法则可进行内容前景的自定义绘制。内容前景位于内容和前景之间，适用于需要在组件内容之上、组件前景之下添加绘制内容的场景。该接口的DrawContext中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-extension-drawModifier.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | 是 | 图形绘制上下文，提供canvas（画布对象）和size（绘制区域尺寸）等属性，用于在自定义绘制方法中执行具体的绘制操作。 |

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。

## drawOverlay

```TypeScript
drawOverlay(drawContext: DrawContext): void
```

自定义绘制遮罩层的接口，若重载该方法则可进行遮罩层的自定义绘制。遮罩层是最上层的绘制层级，适用于需要在组件最上层添加遮罩效果（如高亮、蒙版等）的场景。该接口的DrawContext中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-extension-drawModifier.md#调整自定义绘制canvas的变换矩阵)。

自定义绘制包含五个层级：内容背景层、内容层、内容前景层、前景层和悬浮层。  
- 前景层和悬浮层在子节点之后绘制。  
- 悬浮层与前景层的区别在于：悬浮层可以在组件的边界范围外进行绘制。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](arkts-arkui-common-comp-drawcontext-t.md) | 是 | 图形绘制上下文，提供canvas（画布对象）和size（绘制区域尺寸）等属性，用于在自定义绘制方法中执行具体的绘制操作。 |

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

主动触发重绘的接口，开发者无需也无法重载，调用会触发所绑定组件的重绘。当自定义绘制所依赖的属性（如尺寸、颜色、位置等）发生变化时（例如在动画过程中动态更新绘制参数），需要调用该方法使最新的绘制效果生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考[示例1（通过DrawModifier进行自定义绘制）](#示例1通过drawmodifier进行自定义绘制)。
