# SpotLight

聚光灯类型，继承自Light。聚光灯会朝某个方向发出锥形光，强度随着圆锥角度的衰减由innerAngle和outerAngle两个参数定义。另外与点光源类似，强度也会随着距离光源位置的增加而衰减。

> **注意：**
> 
> 用户需要保证设置的innerAngle与outerAngle值是合理的。
> 当outerAngle设置的值大于PI/2时，内部会强制其等于PI/2。
> 当outerAngle设置的值小于innerAngle时，内部会强制其等于innerAngle。
@extends Light @interface SpotLight

**继承/实现关系：** SpotLight extends [Light](arkts-arkgraphics3d-scenenodes-light-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## innerAngle

```TypeScript
innerAngle?: number
```

从聚光灯中心到开始衰减的角度，对应圆锥的半顶角，在这个圆锥体内光强不随角度衰减。单位为弧度（rad），默认值为0。 设置的值必须大于等于0，小于等于outerAngle。

**类型：** number

**默认值：** 0

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## outerAngle

```TypeScript
outerAngle?: number
```

从聚光灯中心到衰减结束的角度，对应圆锥的半顶角，在这个圆锥体外不再有光强度。单位为弧度（rad），默认值为PI/4。 设置的值必须大于等于innerAngle，小于等于PI/2。

**类型：** number

**默认值：** PI / 4.0

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D
