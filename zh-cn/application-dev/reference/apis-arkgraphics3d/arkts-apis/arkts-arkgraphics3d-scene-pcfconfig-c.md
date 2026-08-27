# PCFConfig

PCF（Percentage Closer Filtering，百分比邻近过滤）软阴影配置类，继承自SoftShadowConfig。

**继承/实现关系：** PCFConfig extends [SoftShadowConfig](arkts-arkgraphics3d-scene-softshadowconfig-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowSampleCount

```TypeScript
set shadowSampleCount(value: number | undefined)
```

采样数量，决定了每个像素采样阴影图的次数，数量越多，阴影质量越高，但性能开销越大。 默认值为16。 取值范围：0 ~ 64。  
- 超出此范围的值会被自动限制到最近的有效边界值（例如65实际按64处理）。  
- 设置为0时，将不进行PCF采样，无阴影效果。  
- 设置为undefined时，恢复默认值16进行渲染。

**类型：** number

**默认值：** 16

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowSampleRadius

```TypeScript
set shadowSampleRadius(value: number | undefined)
```

采样半径，决定了阴影边缘模糊的范围，半径越大，阴影边缘越柔和。采样半径过大会导致阴影过度模糊，失去阴影形状特征。 默认值为5.0。 取值范围：&gt;= 0。  
- 设置为0时，将不进行PCF采样，无阴影效果。  
- 设置为undefined时，恢复默认值5.0进行渲染。

**类型：** number

**默认值：** 5.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D
