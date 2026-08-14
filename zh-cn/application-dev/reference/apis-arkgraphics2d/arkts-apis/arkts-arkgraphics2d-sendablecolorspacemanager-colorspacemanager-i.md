# ColorSpaceManager

当前可共享的色彩管理实例。ColorSpaceManager是用于管理和操作色域对象的核心类，提供了获取色域类型、白点值、gamma值等功能，并支持在ArkTS并发实例间传递。 下列API示例中都需先使用[create()](arkts-arkgraphics2d-sendablecolorspacemanager-create-f.md#create)获取到ColorSpaceManager实例，再通过此实例调用对应方法。

**继承/实现关系：** ColorSpaceManager extends [ISendable](arkts-arkgraphics2d-sendablecolorspacemanager-isendable-t.md#ISendable)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-sendableColorSpaceManager-interface ColorSpaceManager--><!--Device-sendableColorSpaceManager-interface ColorSpaceManager-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## getColorSpaceName

```TypeScript
getColorSpaceName(): colorSpaceManager.ColorSpace
```

获取色域类型。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ColorSpaceManager-getColorSpaceName(): colorSpaceManager.ColorSpace--><!--Device-ColorSpaceManager-getColorSpaceName(): colorSpaceManager.ColorSpace-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| colorSpaceManager.ColorSpace | 返回色域类型枚举值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 12 - 22 |

## 示例

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ColorSpaceManager-getGamma(): number--><!--Device-ColorSpaceManager-getGamma(): number-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回色域gamma值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 12 - 22 |

## 示例

```TypeScript
// 获取色域gamma值
let gamma: number = colorSpace.getGamma();
```

## getWhitePoint

```TypeScript
getWhitePoint(): collections.Array<number>
```

获取色域白点值，返回色度坐标[x, y]，表示色彩空间中白色点的坐标位置。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ColorSpaceManager-getWhitePoint(): collections.Array<number>--><!--Device-ColorSpaceManager-getWhitePoint(): collections.Array<number>-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| collections.Array&lt;number&gt; | 返回色域白点值[x, y]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [18600001](../errorcode-colorspace-manager.md#18600001-参数值异常) | The parameter value is abnormal.<br>**适用版本：** 12 - 22 |

## 示例

```TypeScript
import { collections } from '@kit.ArkTS';
// 获取色域白点值[x, y]
let point: collections.Array<number> = colorSpace.getWhitePoint();
```

