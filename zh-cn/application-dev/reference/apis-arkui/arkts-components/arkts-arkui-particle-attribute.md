# Particle属性/事件

除支持通用属性外还支持以下属性：

**继承/实现关系：** ParticleAttribute extends CommonMethod<ParticleAttribute>

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## disturbanceFields

```TypeScript
disturbanceFields(fields: Array<DisturbanceFieldOptions>)
```

设置扰动场。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;[DisturbanceFieldOptions](arkts-arkui-disturbancefieldoptions-i.md)&gt; | 是 | 扰动场数组。 |

## emitter

```TypeScript
emitter(value: Array<EmitterProperty>)
```

支持发射器位置动态更新

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[EmitterProperty](arkts-arkui-emitterproperty-i.md)&gt; | 是 | 需要更新的emitter参数数组 |

## rippleFields

```TypeScript
rippleFields(fields: Array<RippleFieldOptions> | undefined)
```

设置粒子波动场。波动场会对影响范围内的粒子施加按波形变化的力，产生类似波纹扩散的效果。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;[RippleFieldOptions](arkts-arkui-ripplefieldoptions-i.md)&gt; \| undefined | 是 | 粒子波动场数组。通过数组形式可以设置多个粒子波动场。当设置为undefined时，表示无波动场。 |

## velocityFields

```TypeScript
velocityFields(fields: Array<VelocityFieldOptions> | undefined)
```

设置粒子速度场。速度场会对影响范围内的粒子施加一个力，使粒子在原有速度的基础上叠加速度场指定的速度。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;[VelocityFieldOptions](arkts-arkui-velocityfieldoptions-i.md)&gt; \| undefined | 是 | 粒子速度场数组。通过数组形式可设置多个粒子速度场。设置为undefined时表示无速度场。 |
