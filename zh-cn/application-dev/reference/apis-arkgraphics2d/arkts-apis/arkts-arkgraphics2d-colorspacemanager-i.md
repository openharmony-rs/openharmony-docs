# ColorSpaceManager

当前可共享的色彩管理实例。
下列API示例中都需先使用[create()](arkts-arkgraphics2d-create-f.md#create-1)获取到
ColorSpaceManager实例，再通过此实例调用对应方法。

**继承/实现关系：** ColorSpaceManager extends [ISendable](arkts-arkgraphics2d-isendable-t.md)

**起始版本：** 12

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## getColorSpaceName

```TypeScript
getColorSpaceName(): colorSpaceManager.ColorSpace
```

获取色域类型。

**起始版本：** 12

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| colorSpaceManager.ColorSpace | Color space type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 12 - 22 |

**示例：**

```TypeScript
// 获取色域类型
let spaceName: colorSpaceManager.ColorSpace = colorSpace.getColorSpaceName();

```

## getGamma

```TypeScript
getGamma(): number
```

获取色域gamma值。

**起始版本：** 12

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回色域gamma值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 12 - 22 |

**示例：**

```TypeScript
// 获取色域gamma值
let gamma: number = colorSpace.getGamma();

```

## getWhitePoint

```TypeScript
getWhitePoint(): collections.Array<number>
```

获取色域白点值。

**起始版本：** 12

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| collections.Array&lt;number&gt; | Coordinates [x, y] of the white point. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 12 - 22 |

**示例：**

```TypeScript
import { collections } from '@kit.ArkTS';
// 获取色域白点值[x, y]
let point: collections.Array<number> = colorSpace.getWhitePoint();

```

