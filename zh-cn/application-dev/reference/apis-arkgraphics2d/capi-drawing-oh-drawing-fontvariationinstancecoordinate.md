# OH_Drawing_FontVariationInstanceCoordinate

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

```c
typedef struct {...} OH_Drawing_FontVariationInstanceCoordinate
```

## 概述

可变字体属性键值对。

**起始版本：** 24

**相关模块：** [Drawing](capi-drawing.md)

**所在头文件：** [drawing_text_font_descriptor.h](capi-drawing-text-font-descriptor-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* axisKey | 可变字体属性键值对中的关键字标识的字符串。 |
| double value | 可变字体属性键值对的值。 |