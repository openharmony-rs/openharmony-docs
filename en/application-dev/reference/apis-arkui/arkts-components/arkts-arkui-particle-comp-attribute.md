# Particle properties/events

Defines the Particle component attribute functions.

@extends CommonMethod&lt;ParticleAttribute&gt;

**Inheritance/Implementation:** ParticleAttribute extends CommonMethod<ParticleAttribute>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disturbanceFields

```TypeScript
disturbanceFields(fields: Array<DisturbanceFieldOptions>)
```

Sets the disturbance fields.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;[DisturbanceFieldOptions](arkts-arkui-disturbancefieldoptions-i.md)&gt; | Yes | Array of disturbance fields. |

## emitter

```TypeScript
emitter(value: Array<EmitterProperty>)
```

Sets the emitter parameters.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Array&lt;[EmitterProperty](arkts-arkui-emitterproperty-i.md)&gt; | Yes | Array of emitter parameters to set. |

## rippleFields

```TypeScript
rippleFields(fields: Array<RippleFieldOptions> | undefined)
```

Sets the particle wave field. The wave field applies a force that changes according to the waveform to particles within the affected range, producing an effect similar to the spreading of ripples.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;[RippleFieldOptions](arkts-arkui-ripplefieldoptions-i.md)&gt; &#124; undefined | Yes | Particle wave field array. You can set multiple particle wave fields in array form. If this parameter is set to undefined, no wave field is available. |

## velocityFields

```TypeScript
velocityFields(fields: Array<VelocityFieldOptions> | undefined)
```

Sets the particle velocity field. The velocity field applies a force to particles within the affected range, so that the particles move at the velocity specified by the velocity field in addition to their original velocity.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;[VelocityFieldOptions](arkts-arkui-velocityfieldoptions-i.md)&gt; &#124; undefined | Yes | Particle velocity field array. You can set multiple particle velocity fields in array form. If this parameter is set to undefined, there is no velocity field. |
