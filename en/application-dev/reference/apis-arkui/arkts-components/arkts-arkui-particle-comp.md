# Particle

Defines Particle Component.

## Particle

```TypeScript
Particle(particles: Particles<
      PARTICLE,
      COLOR_UPDATER,
      OPACITY_UPDATER,
      SCALE_UPDATER,
      ACC_SPEED_UPDATER,
      ACC_ANGLE_UPDATER,
      SPIN_UPDATER
    >)
```

create a particle array.

Anonymous Object Rectification.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| particles | [Particles](arkts-arkui-particles-i.md)&lt;PARTICLE, COLOR_UPDATER, OPACITY_UPDATER, SCALE_UPDATER, ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER, SPIN_UPDATER&gt; | Yes | Array of particles. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AccelerationOptions](arkts-arkui-accelerationoptions-i.md) | Particle acceleration. |
| [DisturbanceFieldOptions](arkts-arkui-disturbancefieldoptions-i.md) | Defines particle disturbance Field params. |
| [EmitterOptions](arkts-arkui-emitteroptions-i.md) | Particle emitter configuration. |
| [EmitterParticleOptions](arkts-arkui-emitterparticleoptions-i.md) | Defines parameters of particles used by emitters. |
| [EmitterProperty](arkts-arkui-emitterproperty-i.md) | Defines the emitter property. |
| [FieldRegion](arkts-arkui-fieldregion-i.md) | Defines the area information of the particle field. |
| [ImageParticleParameters](arkts-arkui-imageparticleparameters-i.md) | Defines the parameters for an image-like particle. @interface ImageParticleParameters |
| [ParticleAnnulusRegion](arkts-arkui-particleannulusregion-i.md) | Configures the annular emitter area. |
| [ParticleColorOptions](arkts-arkui-particlecoloroptions-i.md) | The color changes randomly, with the per-second change difference being a value randomly generated from the range. The target color is obtained by applying the change difference to the current color value of each of the R, G, B, A channels. |
| [ParticleColorPropertyOptions](arkts-arkui-particlecolorpropertyoptions-i.md) | Defines the particle color property updater configs which can support generics. @interface ParticleColorPropertyOptions |
| [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particlecolorpropertyupdaterconfigs-i.md) | Defines the particle color property updater configs. @interface ParticleColorPropertyUpdaterConfigs |
| [ParticleColorUpdaterOptions](arkts-arkui-particlecolorupdateroptions-i.md) | How the color property is updated. |
| [ParticleConfigs](arkts-arkui-particleconfigs-i.md) | Defines the particle configs. |
| [ParticleOptions](arkts-arkui-particleoptions-i.md) | Defines the ParticleOptions Interface. |
| [ParticlePropertyAnimation](arkts-arkui-particlepropertyanimation-i.md) | Defines the particle property lifecycle. @interface ParticlePropertyAnimation |
| [ParticlePropertyOptions](arkts-arkui-particlepropertyoptions-i.md) | Defines the particle property Options. @interface ParticlePropertyOptions |
| [ParticlePropertyUpdaterConfigs](arkts-arkui-particlepropertyupdaterconfigs-i.md) | Defines the particle property updater configs. @interface ParticlePropertyUpdaterConfigs |
| [Particles](arkts-arkui-particles-i.md) | Defines the particle array. |
| [ParticleUpdaterOptions](arkts-arkui-particleupdateroptions-i.md) | Defines the particle updater options. |
| [PointParticleParameters](arkts-arkui-pointparticleparameters-i.md) | Defines the parameters for a point-like particle. @interface PointParticleParameters |
| [RippleFieldOptions](arkts-arkui-ripplefieldoptions-i.md) | Defines ripple field options. |
| [VelocityFieldOptions](arkts-arkui-velocityfieldoptions-i.md) | Parameter used to describe the velocity field of particles. |
| [VelocityOptions](arkts-arkui-velocityoptions-i.md) | Defines velocity options. |

### Types

| Name | Description |
| --- | --- |
| [ParticleTuple](arkts-arkui-particletuple-t.md) | Defines a pair of given type for particle. |
| [PositionT](arkts-arkui-positiont-t.md) | Defines the PositionT type. |
| [SizeT](arkts-arkui-sizet-t.md) | Defines the SizeT type. |
| [Vector2T](arkts-arkui-vector2t-t.md) | Defines the Vector2T type. The Vector2T type contains two attribute values: x and y. |

### Enums

| Name | Description |
| --- | --- |
| [DistributionType](arkts-arkui-distributiontype-e.md) | Enumerates the color distribution types of a particle. |
| [DisturbanceFieldShape](arkts-arkui-disturbancefieldshape-e.md) | Defines particle disturbance shape. |
| [ParticleEmitterShape](arkts-arkui-particleemittershape-e.md) | Enumerates the emitter shapes of a particle. |
| [ParticleType](arkts-arkui-particletype-e.md) | Enumerates the particle types. |
| [ParticleUpdater](arkts-arkui-particleupdater-e.md) | Enumerates the updater types of a particle. |

## Examples

```TypeScript
### Example 1: Initializing Particles with Circular Shapes

This example demonstrates the basic usage of particle animations by initializing particles with circular shapes.


```

```TypeScript
### Example 2: Initializing Particles with Images

Describes the basic usage of particle animation, where particles are initialized through images. This example configures two different types of image particles to demonstrate the combined effect of multiple particle types.


```

```TypeScript
### Example 3: Changing Motion Trajectories with the Particle Disturbance Field

This example demonstrates the effect of particle motion trajectory changes under the interference of a disturbance field.


```

```TypeScript
### Example 4: Adjusting the Emitter Position

This example demonstrates how to adjust the position of the particle emitter through emitter().


```

```TypeScript
### Example 5: Creating an Annulus Emitter

This example demonstrates how to create a annulus emitter, where particles are statically emitted across the entire annulus range (from the start angle 0 to the end angle 360).


```

```TypeScript
### Example 6: Annulus Emitter Update

This example describes the basic usage of updating the annulus emitter of a particle animation.


```

```TypeScript
### Example 7: Setting Ripple Field and Velocity Field

Since API version 22, particle ripple fields and velocity fields can be set. This example demonstrates how to set a particle ripple field through the rippleFields API to produce an effect similar to ripple diffusion. The velocityFields API is used to set a particle velocity field, so that the velocity specified by the velocity field is superimposed on the original velocity of the particles.
```
