# Particle properties/events

```TypeScript
declare class ParticleAttribute extends CommonMethod<ParticleAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp.md) are supported.

**Inheritance/Implementation:** ParticleAttribute extends CommonMethod&lt;ParticleAttribute&gt;

**Since:** 10

<!--Device-unnamed-declare class ParticleAttribute extends CommonMethod<ParticleAttribute>--><!--Device-unnamed-declare class ParticleAttribute extends CommonMethod<ParticleAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disturbanceFields

```TypeScript
disturbanceFields(fields: Array<DisturbanceFieldOptions>)
```

Sets the disturbance fields.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParticleAttribute-disturbanceFields(fields: Array<DisturbanceFieldOptions>): ParticleAttribute--><!--Device-ParticleAttribute-disturbanceFields(fields: Array<DisturbanceFieldOptions>): ParticleAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;[DisturbanceFieldOptions](arkts-arkui-particle-comp-disturbancefieldoptions-i.md)&gt; | Yes | Array of disturbance fields. Used to set the disturbance effect on the particle motion trajectory. By configuring multiple disturbance fields, repulsive or attractive forces can be applied to particles to change their motion trajectories. |

## emitter

```TypeScript
emitter(value: Array<EmitterProperty>)
```

Supports dynamic update of emitter properties. Use the index in **EmitterProperty** to specify the emitter to update (based on the array index of the emitter in the initialization parameters), and dynamically update the emission rate, position, size, and annular area parameters of the emitter. You must first create a particle animation and configure the emitter through the **Particle** API, and then dynamically update the parameters of the corresponding emitter through the **emitter()** property. The **emitter()** property only updates the parameters of existing emitters and cannot add new emitters.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParticleAttribute-emitter(value: Array<EmitterProperty>): ParticleAttribute--><!--Device-ParticleAttribute-emitter(value: Array<EmitterProperty>): ParticleAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[EmitterProperty](arkts-arkui-particle-comp-emitterproperty-i.md)&gt; | Yes | Array of emitter parameters to be updated. |

## rippleFields

```TypeScript
rippleFields(fields: Array<RippleFieldOptions> | undefined)
```

Sets the particle ripple field. The ripple field applies a force that changes in a waveform manner to particles within its influence range, producing an effect similar to ripple diffusion.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ParticleAttribute-rippleFields(fields: Array<RippleFieldOptions> | undefined): ParticleAttribute--><!--Device-ParticleAttribute-rippleFields(fields: Array<RippleFieldOptions> | undefined): ParticleAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;[RippleFieldOptions](arkts-arkui-particle-comp-ripplefieldoptions-i.md)&gt; &#124; undefined | Yes | Array of particle ripple fields. Multiple particle ripple fields can be set in the array form. When set to **undefined**, it indicates no ripple field. |

## velocityFields

```TypeScript
velocityFields(fields: Array<VelocityFieldOptions> | undefined)
```

Sets the particle velocity field. The velocity field applies a force to particles within its influence range, so that the velocity specified by the velocity field is superimposed on the original velocity of the particles.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ParticleAttribute-velocityFields(fields: Array<VelocityFieldOptions> | undefined): ParticleAttribute--><!--Device-ParticleAttribute-velocityFields(fields: Array<VelocityFieldOptions> | undefined): ParticleAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;[VelocityFieldOptions](arkts-arkui-particle-comp-velocityfieldoptions-i.md)&gt; &#124; undefined | Yes | Array of particle velocity fields. Multiple particle velocity fields can be set in array form. When set to **undefined**, it indicates no velocity field. |
