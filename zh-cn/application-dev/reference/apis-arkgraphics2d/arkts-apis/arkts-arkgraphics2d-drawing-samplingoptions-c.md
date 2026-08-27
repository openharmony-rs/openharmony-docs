# SamplingOptions

采样选项对象，用于配置图像采样时的过滤模式，控制图像缩放或变换过程中的像素采样方式。典型使用场景为在Canvas上绘制图像（如drawImage）时，以不同过滤模式决定图像的采样质量与渲染效果。

> **说明：**
> 
> - 本Class首批接口从API version 12开始支持。
> 
> - 本模块使用屏幕物理像素单位px。
> 
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

构造一个新的采样选项对象，[FilterMode](arkts-arkgraphics2d-drawing-filtermode-e.md)的默认值为FILTER_MODE_NEAREST。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let matrix = new drawing.Matrix();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
```

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions();
  }
}
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
let typefaceArgument = new drawing.TypefaceArguments();
```

## constructor

```TypeScript
constructor(filterMode: FilterMode)
```

构造一个新的采样选项对象，可通过指定filterMode参数适配不同的图像采样场景。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filterMode | [FilterMode](arkts-arkgraphics2d-drawing-filtermode-e.md) | 是 | 过滤模式，用于指定图像采样时的过滤算法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions(drawing.FilterMode.FILTER_MODE_NEAREST);
  }
}
```
