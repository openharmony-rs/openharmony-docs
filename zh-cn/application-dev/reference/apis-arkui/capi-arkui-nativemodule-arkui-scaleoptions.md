# ArkUI_ScaleOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_ScaleOptions
```

## 概述

定义组件转场时的缩放效果对象。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float x | x轴的缩放倍数。x>1时以x轴方向放大，0<x<1时以x轴方向缩小，x=0时表示在x轴方向缩小成0，x=1时表示在x轴方向缩放倍数是1，x<0时沿x轴反向并缩放。 |
| float y | y轴的缩放倍数。y>1时以y轴方向放大，0<y<1时以y轴方向缩小，y=0时表示在y轴方向缩小成0，y=1时表示在y轴方向缩放倍数是1，y<0时沿y轴反向并缩放。 |
| float z | 当前为二维显示，该参数无效 。 |
| float centerX | 变换中心点x轴坐标。表示组件变换中心点（即锚点）的x方向坐标，单位为vp。 |
| float centerY | 变换中心点y轴坐标。表示组件变换中心点（即锚点）的y方向坐标，单位为vp。 |


