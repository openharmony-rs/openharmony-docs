# Particle属性/事件

```TypeScript
declare class ParticleAttribute extends CommonMethod<ParticleAttribute>
```

除支持[通用属性](arkts-arkui-common-comp.md#common)外还支持以下属性：

支持[通用事件](arkts-arkui-common-comp.md#common)。

@extends CommonMethod&lt;ParticleAttribute&gt;

**继承/实现关系：** ParticleAttribute extends CommonMethod<ParticleAttribute>

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disturbanceFields

```TypeScript
disturbanceFields(fields: Array<DisturbanceFieldOptions>)
```

设置扰动场。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;[DisturbanceFieldOptions](arkts-arkui-particle-comp-disturbancefieldoptions-i.md)&gt; | 是 | 扰动场数组。用于设置粒子运动轨迹的干扰效果，通过配置多个扰动场可对粒子施加排斥力或吸引力，改变粒子的运动轨迹。 |

## emitter

```TypeScript
emitter(value: Array<EmitterProperty>)
```

支持发射器属性动态更新。通过EmitterProperty中的index指定需要更新的发射器（按初始化参数中发射器的数组索引），可动态更新发射器的发射速率、位置、大小和环形区域参数。必须先通过Particle接口创建粒子动画并配置发射器，再通过emitter()属性动态更新对应发射器的参数，emitter()属性仅更新已有发射器的参数，不能新增发射器。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[EmitterProperty](arkts-arkui-particle-comp-emitterproperty-i.md)&gt; | 是 | 需要更新的发射器参数数组。 |

## rippleFields

```TypeScript
rippleFields(fields: Array<RippleFieldOptions> | undefined)
```

设置粒子波动场。波动场会对影响范围内的粒子施加按波形变化的力，产生类似波纹扩散的效果。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;[RippleFieldOptions](arkts-arkui-particle-comp-ripplefieldoptions-i.md)&gt; &#124; undefined | 是 | 粒子波动场数组。通过数组形式可以设置多个粒子波动场。当设置为undefined时，表示无波动场。 |

## velocityFields

```TypeScript
velocityFields(fields: Array<VelocityFieldOptions> | undefined)
```

设置粒子速度场。速度场会对影响范围内的粒子施加一个力，使粒子在原有速度的基础上叠加速度场指定的速度。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;[VelocityFieldOptions](arkts-arkui-particle-comp-velocityfieldoptions-i.md)&gt; &#124; undefined | 是 | 粒子速度场数组。通过数组形式可设置多个粒子速度场。设置为undefined时表示无速度场。 |
