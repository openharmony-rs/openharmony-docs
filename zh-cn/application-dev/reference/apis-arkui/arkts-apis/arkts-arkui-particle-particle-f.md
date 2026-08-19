# Particle

## Particle

```TypeScript
@ComponentBuilder
export declare function Particle(
    particles: Particles, 
): ParticleAttribute
```

Defines Particle Component

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Particle(    particles: Particles, ): ParticleAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Particle(    particles: Particles, ): ParticleAttribute-End-->

**系统能力：** 
- API版本23+：SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| particles | [Particles](arkts-arkui-particle-particles-i.md) | 是 | particle constructor options<br>**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ParticleAttribute |  |


## Particle

```TypeScript
@Builder
export declare function Particle(
  style_: CustomBuilderT<ParticleAttribute>,
): ParticleAttribute
```

Defines Particle

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Particle(  style_: CustomBuilderT<ParticleAttribute>,): ParticleAttribute--><!--Device-unnamed-@Builderexport declare function Particle(  style_: CustomBuilderT<ParticleAttribute>,): ParticleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ParticleAttribute&gt; | 是 | Particle attribute instance |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ParticleAttribute |  |

