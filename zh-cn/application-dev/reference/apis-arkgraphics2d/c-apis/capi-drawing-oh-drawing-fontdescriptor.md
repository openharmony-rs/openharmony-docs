# OH_Drawing_FontDescriptor

```c
typedef struct OH_Drawing_FontDescriptor {...} OH_Drawing_FontDescriptor
```

## 概述

描述系统字体详细信息的结构体。

<!--Device-struct OH_Drawing_FontDescriptor {...}--><!--Device-struct OH_Drawing_FontDescriptor {...}-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-arkgraphics2d-drawing.md)

**所在头文件：** [drawing_text_typography.h](capi-drawing-text-typography-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* path | 系统字体的文件路径。<br><!--Device-char* path--><!--Device-char* path-End--> |
| char* postScriptName | 唯一标识字体的名称。<br><!--Device-char* postScriptName--><!--Device-char* postScriptName-End--> |
| char* fullName | 系统字体的名称。<br><!--Device-char* fullName--><!--Device-char* fullName-End--> |
| char* fontFamily | 系统字体的字体家族。<br><!--Device-char* fontFamily--><!--Device-char* fontFamily-End--> |
| char* fontSubfamily | 系统字体的子字体家族。<br><!--Device-char* fontSubfamily--><!--Device-char* fontSubfamily-End--> |
| int weight | 系统字体的粗细程度。<br><!--Device-int weight--><!--Device-int weight-End--> |
| int width | 系统字体的宽窄风格属性。<br><!--Device-int width--><!--Device-int width-End--> |
| int italic | 系统字体倾斜度。<br><!--Device-int italic--><!--Device-int italic-End--> |
| bool monoSpace | 系统字体是否等宽。true表示字体等宽，false表示字体非等宽。<br><!--Device-bool monoSpace--><!--Device-bool monoSpace-End--> |
| bool symbolic | 系统字体是否支持符号字体。true表示支持符号字体，false表示不支持符号字体。<br><!--Device-bool symbolic--><!--Device-bool symbolic-End--> |


