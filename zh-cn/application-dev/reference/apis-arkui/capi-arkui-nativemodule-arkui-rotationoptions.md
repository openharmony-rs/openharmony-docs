# ArkUI_RotationOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_RotationOptions
```

## 概述

定义组件转场时的旋转效果对象。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float x | 横向的旋转向量分量，与y、z共同定义旋转轴方向。取值范围：(-∞, +∞)。 |
| float y | 纵向的旋转向量分量，与x、z共同定义旋转轴方向。取值范围：(-∞, +∞)。 |
| float z | 竖向的旋转向量分量，与x、y共同定义旋转轴方向。取值范围：(-∞, +∞)。 |
| float angle | 旋转角度，单位为：度（°）。取值范围：(-∞, +∞)。取值为正时沿由(x,y,z)确定的旋转轴方向顺时针转动，取值为负时沿该旋转轴方向逆时针转动。 |
| float centerX | 3D旋转中心点的x轴分量，单位为vp。取值范围：(-∞, +∞)。 |
| float centerY | 3D旋转中心点的y轴分量，单位为vp。取值范围：(-∞, +∞)。 |
| float centerZ | 变换中心点z轴坐标，即3D旋转中心点的z轴分量，单位为px。取值为0时旋转中心在组件所在平面，取值大于0时旋转中心向观察者方向偏移，取值小于0时旋转中心向远离观察者方向偏移。3D旋转效果的呈现受perspective参数影响，需配合perspective参数设置使用。 |
| float perspective | 视距，即视点到z=0平面的距离，相机放置的z轴坐标，单位为px。。数值大小表示视距，即相机到z=0平面的距离。取值的正负决定了相机观察的方向。当perspective=0，系统会自动计算适合的相机z轴位置，取值为负数。 |


