# Class (SamplingOptions)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

采样选项对象，用于配置图像采样时的过滤模式，控制图像缩放或变换过程中的像素采样方式。典型使用场景为在Canvas上绘制图像（如drawImage）时，以不同过滤模式决定图像的采样质量与渲染效果。

> **说明：**
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor<sup>12+</sup>

constructor()

构造一个新的采样选项对象，[FilterMode](arkts-apis-graphics-drawing-e.md#filtermode12)的默认值为FILTER_MODE_NEAREST。

**系统能力：** SystemCapability.Graphics.Drawing

**示例：**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions();
  }
}
```

## constructor<sup>12+</sup>

constructor(filterMode: FilterMode)

构造一个新的采样选项对象，可通过指定filterMode参数适配不同的图像采样场景。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名     | 类型                   | 必填 | 说明                                 |
| ---------- | --------------------- | ---- | ----------------------------------- |
| filterMode | [FilterMode](arkts-apis-graphics-drawing-e.md#filtermode12)    | 是   | 过滤模式，用于指定图像采样时的过滤算法。                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions(drawing.FilterMode.FILTER_MODE_NEAREST);
  }
}
```