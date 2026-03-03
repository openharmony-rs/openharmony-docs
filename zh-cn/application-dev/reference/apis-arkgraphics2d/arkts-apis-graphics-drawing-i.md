# Interfaces (其他)

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
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

## TextBlobRunBuffer

描述一行文字中具有相同属性的连续字形。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

| 名称      | 类型   | 只读 | 可选 | 说明                      |
| --------- | ------ | ---- | ---- | ------------------------- |
| glyph     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否   | 否   | 存储文字的索引，该参数为整数，传入浮点类型时向下取整。 |
| positionX | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文本的起点x轴坐标，该参数为浮点数。 |
| positionY | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文本的起点y轴坐标，该参数为浮点数。 |

## FontMetrics

描述字形大小和布局的属性信息，同一种字体中的字符属性大致相同。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称    | 类型   | 只读 | 可选 | 说明                                                         |
| ------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| flags<sup>12+</sup>   | ArkTS-Dyn: [FontMetricsFlags](arkts-apis-graphics-drawing-e.md#fontmetricsflags12)<br/>ArkTS-Sta: int | 否   | 是   | 表明哪些字体度量标志有效。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22        |
| top     | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文字最高处到基线之间的最大距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：22                         |
| ascent  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文字最高处到基线之间的距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：22                             |
| descent | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 基线到文字最低处之间的距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：22                             |
| bottom  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 基线到文字最低处之间的最大距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：22                         |
| leading | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 行间距，从上一行文字descent到下一行文字ascent之间的距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本**：22 |
| avgCharWidth<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 平均字符宽度。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22                             |
| maxCharWidth<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 最大字符宽度。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22                             |
| xMin<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否    | 是   | 字体中任意字形边界框最左边沿到原点的水平距离，这个值往往小于零，意味着字形在水平方向上的最小边界。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22                |
| xMax<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 字体中任意字形边界框最右边沿到原点的水平距离，此值多为正数，指示了字形在水平方向上的最大延伸范围。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22        |
| xHeight<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 小写字母x的高度，通常为负值。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22                     |
| capHeight<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 大写字母的高度，通常为负值。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22                      |
| underlineThickness<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 下划线的厚度。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22                                          |
| underlinePosition<sup>12+</sup>  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 文本基线到下划线顶部的垂直距离，通常是正数。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22             |
| strikethroughThickness<sup>12+</sup>  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 文本删除线的厚度，即贯穿文本字符的水平线的宽度。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22    |
| strikethroughPosition<sup>12+</sup>  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 文本基线到底部删除线的垂直距离，通常为负值。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本**：22         |

## FontFeature<sup>20+</sup>

表示字体特征。字体特征是字体内置的排版规则，用于控制字形的显示效果，具体包括连字、替代字形、上下标等功能。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

| 名称    | 类型   | 只读 | 可选 | 说明   |
| ------- | ------ | ---- | ---- | ------------------ |
| name   | string | 否   | 否   | 字体特征的名称。常见的字体特征名称包含liga、frac、case等，需要对应的ttf文件支持才能生效。|
| value | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否 | 否 | 字体特征的数值，浮点数。建议通过字体查看工具或查阅字体文档，确定具体的有效取值范围。|