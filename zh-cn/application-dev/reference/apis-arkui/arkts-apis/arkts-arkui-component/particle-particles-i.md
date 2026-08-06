# Particles

粒子动画的集合。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface Particles--><!--Device-unnamed-export interface Particles-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## particles

```TypeScript
particles: Array<ParticleOptions>
```

粒子动画的集合。每一个的粒子动画（[ParticleOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_）包含粒子发射，同时可配置粒子的颜色、透明度、大小、速度、加速度与旋转速度，详见 [ParticleOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_属性说明。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** Array&lt;ParticleOptions&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Particles-particles: Array<ParticleOptions>--><!--Device-Particles-particles: Array<ParticleOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

