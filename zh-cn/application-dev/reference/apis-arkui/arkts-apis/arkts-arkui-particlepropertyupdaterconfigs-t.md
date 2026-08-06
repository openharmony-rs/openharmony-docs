# ParticlePropertyUpdaterConfigs

```TypeScript
export type ParticlePropertyUpdaterConfigs = undefined | ParticleTuple<double, double> | Array<ParticlePropertyAnimation<double>>
```

设置粒子属性更新器配置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ParticlePropertyUpdaterConfigs = undefined | ParticleTuple<double, double> | Array<ParticlePropertyAnimation<double>>--><!--Device-unnamed-export type ParticlePropertyUpdaterConfigs = undefined | ParticleTuple<double, double> | Array<ParticlePropertyAnimation<double>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| undefined | 无变化。 |
| ParticleTuple&lt;double, double&gt; | 表示变化方式为匀速变化时，每秒的变化差值为设置区间随机生成的值。\_\_\_HTML\_TAG\_USD\_0\_\_\_目标属性值为当前属性值叠加变化差值。如当前属性值为0.2， config取[0.1,1.0]:\_\_\_HTML\_TAG\_USD\_1\_\_\_1、如果变化差值在区间[0.1,1.0]取随机值0.5，则目标属性值为0.2+0.5 = 0.7；\_\_\_HTML\_TAG\_USD\_2\_\_\_2、变化差值也可以取负值。如当前属性值为0.2，config为 [-3.0,2.0],如果变化差值在区间[-3.0,2.0]取随机值-2.0，则目标属性值为0.2-2.0 = -1.8。 \_\_\_HTML\_TAG\_USD\_3\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_4\_\_\_config配置的是变化差值的取值范围，差值的最大最小值没有约束。但是如果当前属性值叠加差值大于属性最大值，目标属性值取属性最大值；如果当前属性值叠加差值小于属性最小值，目标属性值取属性最小值。T为number。 \_\_\_HTML\_TAG\_USD\_5\_\_\_例如：opacity的取值范围[0.0,1.0]则当当前属性值叠加差值超过1.0，则取1.0。 |
| Array&lt;ParticlePropertyAnimation&lt;double&gt;&gt; | 表示变化方式为曲线变化时，属性变化的配置。数组类型表示当前属性可以设置多段动画，如0ms-3000ms，3000ms- 5000ms，5000ms-8000ms分别设置动画。 |

