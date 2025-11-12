# Class (MaskFilter)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

蒙版滤镜对象。

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlurMaskFilter<sup>12+</sup>

ArkTS-Dyn: static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter

ArkTS-Sta: static createBlurMaskFilter(blurType: BlurType, sigma: double): MaskFilter | undefined

创建具有模糊效果的蒙版滤镜。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名     | 类型                   | 必填 | 说明                                 |
| ---------- | --------------------- | ---- | ----------------------------------- |
| blurType   | [BlurType](arkts-apis-graphics-drawing-e.md#blurtype12) | 是   | 模糊类型。                           |
| sigma      | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 高斯模糊的标准偏差，必须为大于0的浮点数。 |

**返回值：**

| 类型                      | 说明                |
| ------------------------- | ------------------ |
| ArkTS-Dyn: [MaskFilter](arkts-apis-graphics-drawing-MaskFilter.md)<br/>ArkTS-Sta: [MaskFilter](arkts-apis-graphics-drawing-MaskFilter.md) \| undefined | 返回创建的蒙版滤镜对象。创建失败时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10.0);
  }
}
```