# PointLight

```TypeScript
export interface PointLight extends Light
```

点光源类型，继承自[Light](arkts-arkgraphics3d-scenenodes-light-i.md)。

点光源从空间中的单个点向所有方向均匀发射光，强度随着距离光源位置的增加而衰减。

> **注意：**
> 
> 点光源不支持阴影投射，设置[Light](arkts-arkgraphics3d-scenenodes-light-i.md)的shadowEnabled属性不生效。

**继承/实现关系：** PointLight extends [Light](arkts-arkgraphics3d-scenenodes-light-i.md)

**起始版本：** 26.1.0

<!--Device-unnamed-export interface PointLight extends Light--><!--Device-unnamed-export interface PointLight extends Light-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## range

```TypeScript
range?: number
```

点光源影响的最大距离，超过该范围光强为0。单位为世界坐标系下的场景单位（比如cm、m、km等），取值大于0。若未设置此参数或取值小于等于0，系统自动计算一个经验值。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PointLight-range?: double--><!--Device-PointLight-range?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D
