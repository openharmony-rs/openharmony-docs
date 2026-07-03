# Interfaces (其他)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wanyanglan-->
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

**ArkTS-Sta起始版本：** 23

| 名称      | 类型   | 只读 | 可选 | 说明                      |
| --------- | ------ | ---- | ---- | ------------------------- |
| glyph     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否   | 否   | 存储文字的索引，该参数为整数，传入浮点类型时向下取整。 |
| positionX | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文本的起点x轴坐标，该参数为浮点数。 |
| positionY | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文本的起点y轴坐标，该参数为浮点数。 |

## FontMetrics

描述字形大小和布局的属性信息，同一种字体中的字符属性大致相同。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称    | 类型   | 只读 | 可选 | 说明                                                         |
| ------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| flags<sup>12+</sup>   | ArkTS-Dyn: [FontMetricsFlags](arkts-apis-graphics-drawing-e.md#fontmetricsflags12)<br/>ArkTS-Sta: int | 否   | 是   | 表明哪些字体度量标志有效。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23        |
| top     | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 字体中任意字形边界框超出基线上方的最大距离，浮点数。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本：** 23                         |
| ascent  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 文字最高处到基线之间的距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本：** 23                             |
| descent | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 基线到文字最低处之间的距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本：** 23                             |
| bottom  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 字体中任意字形边界框超出基线下方的最大距离，浮点数。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本：** 23                         |
| leading | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 否   | 行间距，从上一行文字descent到下一行文字ascent之间的距离，浮点数。<br/>**ArkTS-Dyn起始版本**：11<br/>**ArkTS-Sta起始版本：** 23 |
| avgCharWidth<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 平均字符宽度，浮点数。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23                             |
| maxCharWidth<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 最大字符宽度，浮点数。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23                             |
| xMin<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否    | 是   | 字体中任意字形边界框最左边沿到原点的水平距离，这个值往往小于零，意味着字形在水平方向上的最小边界。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23                |
| xMax<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 字体中任意字形边界框最右边沿到原点的水平距离，浮点数，此值多为正数，指示了字形在水平方向上的最大延伸范围。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23        |
| xHeight<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 小写字母x顶部相对于基线的垂直偏移量，浮点数，通常为负值。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23                     |
| capHeight<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 大写字母顶部相对于基线的垂直偏移量，浮点数，通常为负值。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23                      |
| underlineThickness<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 下划线的厚度，浮点数。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23                                          |
| underlinePosition<sup>12+</sup>  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 文本基线到下划线顶部的垂直距离，浮点数，通常是正数。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23             |
文本删除线的厚度，即贯穿文本字符的水平线的宽度，浮点数。单位为物理像素px。
| strikethroughPosition<sup>12+</sup>  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否   | 是   | 文本基线到删除线的垂直距离，浮点数，通常为负值。单位为物理像素px。<br/>**ArkTS-Dyn起始版本**：12<br/>**ArkTS-Sta起始版本：** 23         |

## FontFeature<sup>20+</sup>

表示字体特征。字体特征是字体内置的排版规则，用于控制字形的显示效果，具体包括连字、替代字形、上下标等功能。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

| 名称    | 类型   | 只读 | 可选 | 说明   |
| ------- | ------ | ---- | ---- | ------------------ |
| name   | string | 否   | 否   | 字体特征的名称。通常为4个ASCII字符组成的标签（如liga、frac、case等），需对应的ttf文件支持才能生效。建议通过字体查看工具或查阅字体文档，确定有效名称。|
| value | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否 | 否 | 字体特征的数值，浮点数。需要对应的ttf文件支持才能生效。建议通过字体查看工具或查阅字体文档，确定具体的有效取值范围。|