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
| particles | [Particles](arkts-arkui-particle-comp-particles-i.md)&lt;PARTICLE, COLOR_UPDATER, OPACITY_UPDATER, SCALE_UPDATER, ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER, SPIN_UPDATER&gt; | Yes | Array of particles. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AccelerationOptions](arkts-arkui-particle-comp-accelerationoptions-i.md) | Particle acceleration. |
| [DisturbanceFieldOptions](arkts-arkui-particle-comp-disturbancefieldoptions-i.md) | Defines particle disturbance Field params. |
| [EmitterOptions](arkts-arkui-particle-comp-emitteroptions-i.md) | Particle emitter configuration. |
| [EmitterParticleOptions](arkts-arkui-particle-comp-emitterparticleoptions-i.md) | Defines parameters of particles used by emitters. |
| [EmitterProperty](arkts-arkui-particle-comp-emitterproperty-i.md) | Defines the emitter property. |
| [FieldRegion](arkts-arkui-particle-comp-fieldregion-i.md) | Defines the area information of the particle field. |
| [ImageParticleParameters](arkts-arkui-particle-comp-imageparticleparameters-i.md) | Defines the parameters for an image-like particle. @interface ImageParticleParameters |
| [ParticleAnnulusRegion](arkts-arkui-particle-comp-particleannulusregion-i.md) | Configures the annular emitter area. |
| [ParticleColorOptions](arkts-arkui-particle-comp-particlecoloroptions-i.md) | The color changes randomly, with the per-second change difference being a value randomly generated from the range. The target color is obtained by applying the change difference to the current color value of each of the R, G, B, A channels. |
| [ParticleColorPropertyOptions](arkts-arkui-particle-comp-particlecolorpropertyoptions-i.md) | Defines the particle color property updater configs which can support generics. @interface ParticleColorPropertyOptions |
| [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particle-comp-particlecolorpropertyupdaterconfigs-i.md) | Defines the particle color property updater configs. @interface ParticleColorPropertyUpdaterConfigs |
| [ParticleColorUpdaterOptions](arkts-arkui-particle-comp-particlecolorupdateroptions-i.md) | How the color property is updated. |
| [ParticleConfigs](arkts-arkui-particle-comp-particleconfigs-i.md) | Defines the particle configs. |
| [ParticleOptions](arkts-arkui-particle-comp-particleoptions-i.md) | Defines the ParticleOptions Interface. |
| [ParticlePropertyAnimation](arkts-arkui-particle-comp-particlepropertyanimation-i.md) | Defines the particle property lifecycle. @interface ParticlePropertyAnimation |
| [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md) | Defines the particle property Options. @interface ParticlePropertyOptions |
| [ParticlePropertyUpdaterConfigs](arkts-arkui-particle-comp-particlepropertyupdaterconfigs-i.md) | Defines the particle property updater configs. @interface ParticlePropertyUpdaterConfigs |
| [Particles](arkts-arkui-particle-comp-particles-i.md) | Defines the particle array. |
| [ParticleUpdaterOptions](arkts-arkui-particle-comp-particleupdateroptions-i.md) | Defines the particle updater options. |
| [PointParticleParameters](arkts-arkui-particle-comp-pointparticleparameters-i.md) | Defines the parameters for a point-like particle. @interface PointParticleParameters |
| [RippleFieldOptions](arkts-arkui-particle-comp-ripplefieldoptions-i.md) | Defines ripple field options. |
| [VelocityFieldOptions](arkts-arkui-particle-comp-velocityfieldoptions-i.md) | Parameter used to describe the velocity field of particles. |
| [VelocityOptions](arkts-arkui-particle-comp-velocityoptions-i.md) | Defines velocity options. |

### Types

| Name | Description |
| --- | --- |
| [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md) | Defines a pair of given type for particle. |
| [PositionT](arkts-arkui-particle-comp-positiont-t.md) | Defines the PositionT type. |
| [SizeT](arkts-arkui-particle-comp-sizet-t.md) | Defines the SizeT type. |
| [Vector2T](arkts-arkui-particle-comp-vector2t-t.md) | Defines the Vector2T type. The Vector2T type contains two attribute values: x and y. |

### Enums

| Name | Description |
| --- | --- |
| [DistributionType](arkts-arkui-particle-comp-distributiontype-e.md) | Enumerates the color distribution types of a particle. |
| [DisturbanceFieldShape](arkts-arkui-particle-comp-disturbancefieldshape-e.md) | Defines particle disturbance shape. |
| [ParticleEmitterShape](arkts-arkui-particle-comp-particleemittershape-e.md) | Enumerates the emitter shapes of a particle. |
| [ParticleType](arkts-arkui-particle-comp-particletype-e.md) | Enumerates the particle types. |
| [ParticleUpdater](arkts-arkui-particle-comp-particleupdater-e.md) | Enumerates the updater types of a particle. |

## Examples

### Example 1: Initializing Particles with Circular Shapes

This example demonstrates the basic usage of particle animations by initializing particles with circular shapes.



```TypeScript
@Entry
@Component
struct ParticleExample {
  build() {
    Stack() {
      Text()
        .width(300).height(300).backgroundColor(Color.Black)
      Particle({
        particles: [
          {
            emitter: {
              particle: {
                type: ParticleType.POINT, // Particle type.
                config: {
                  radius: 10 // Dot radius.
                },
                count: 500, // Total number of particles.
                lifetime: 10000, // Particle lifecycle, in ms.
                lifetimeRange: 100 // Value range of the particle lifecycle, in ms.
              },
              emitRate: 10, // Number of particles emitted per second.
              position: [0, 0],
              shape: ParticleEmitterShape.RECTANGLE // Emitter shape.
            },
            color: {
              range: [Color.Red, Color.Yellow], // Initial color range.
              distributionType: DistributionType.GAUSSIAN, // Distribution of random initial color values.
              updater: {
                type: ParticleUpdater.CURVE, // Change mode is curve.
                config: [
                  {
                    from: Color.White, // Start value of the change.
                    to: Color.Pink, // End value of the change.
                    startMillis: 0, // Start time.
                    endMillis: 3000, // End time.
                    curve: Curve.EaseIn // Change curve.
                  },
                  {
                    from: Color.Pink,
                    to: Color.Orange,
                    startMillis: 3000,
                    endMillis: 5000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: Color.Orange,
                    to: Color.Pink,
                    startMillis: 5000,
                    endMillis: 8000,
                    curve: Curve.EaseIn
                  },
                ]
              }
            },
            opacity: {
              range: [0.0, 1.0], // The initial particle opacity is randomly generated from [0.0 to 1.0].
              updater: {
                type: ParticleUpdater.CURVE,
                config: [
                  {
                    from: 0.0,
                    to: 1.0,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: 1.0,
                    to: 0.0,
                    startMillis: 5000,
                    endMillis: 10000,
                    curve: Curve.EaseIn
                  }
                ]
              }
            },
            scale: {
              range: [0.0, 0.0],
              updater: {
                type: ParticleUpdater.CURVE,
                config: [
                  {
                    from: 0.0,
                    to: 0.5,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  }
                ]
              }
            },
            acceleration: {
              // Configuration of the acceleration, which changes in two dimensions: magnitude and direction. speed indicates the acceleration magnitude, and angle indicates the acceleration direction.
              speed: {
                range: [3, 9],
                updater: {
                  type: ParticleUpdater.RANDOM, // The change mode of Speed is random uniform change.
                  config: [1, 20]
                }
              },
              angle: {
                range: [90, 90]
              }
            }

          }
        ]
      }).width(300).height(300)
    }.width('100%').height('100%').align(Alignment.Center)
  }
}
```

### Example 2: Initializing Particles with Images

Describes the basic usage of particle animation, where particles are initialized through images. This example configures two different types of image particles to demonstrate the combined effect of multiple particle types.



```TypeScript
@Entry
@Component
struct ParticleExample {
  @State
  myCount: number = 100

  // Reduce duplicate code through parameterized configuration. imageSrc is the image resource, scaleTo is the target scale value, and durationMs is the animation duration.
  private createImageParticle(imageSrc: ResourceStr, scaleTo: number, durationMs: number)
    : ParticleOptions<ParticleType.IMAGE, ParticleUpdater.CURVE, ParticleUpdater.CURVE,
  ParticleUpdater.CURVE, ParticleUpdater.CURVE, ParticleUpdater.CURVE, ParticleUpdater.CURVE>
  {
    return {
      emitter: {
        particle: {
          type: ParticleType.IMAGE,
          config: {
            src: imageSrc,
            size: [10, 10]
          },
          count: this.myCount,
          lifetime: 10000,
          lifetimeRange: 100
        },
        emitRate: 3,
        shape: ParticleEmitterShape.CIRCLE
      },
      color: {
        range: [Color.White, Color.White]
      },
      opacity: {
        range: [1.0, 1.0],
        updater: {
          type: ParticleUpdater.CURVE,
          config: [
            { from: 0, to: 1.0, startMillis: 0, endMillis: 6000 },
            { from: 1.0, to: 0, startMillis: 6000, endMillis: 10000 }
          ]
        }
      },
      scale: {
        range: [0.1, 1.0],
        updater: {
          type: ParticleUpdater.CURVE,
          config: [
            { from: 0, to: scaleTo, startMillis: 0, endMillis: durationMs, curve: Curve.EaseIn }
          ]
        }
      },
      acceleration: {
        speed: {
          range: [3, 9],
          updater: {
            type: ParticleUpdater.CURVE,
            config: [
              { from: 10, to: 20, startMillis: 0, endMillis: 3000, curve: Curve.EaseIn },
              { from: 10, to: 2, startMillis: 3000, endMillis: 8000, curve: Curve.EaseIn }
            ]
          }
        },
        angle: {
          range: [0, 180],
          updater: {
            type: ParticleUpdater.CURVE,
            config: [
              { from: 1, to: 2, startMillis: 0, endMillis: 1000, curve: Curve.EaseIn },
              { from: 50, to: -50, startMillis: 1000, endMillis: 3000, curve: Curve.EaseIn },
              { from: 3, to: 5, startMillis: 3000, endMillis: durationMs, curve: Curve.EaseIn }
            ]
          }
        }
      },
      spin: {
        range: [0.1, 1.0],
        updater: {
          type: ParticleUpdater.CURVE,
          config: [
            { from: 0, to: 360, startMillis: 0, endMillis: durationMs, curve: Curve.EaseIn }
          ]
        }
      },
    }
  }

  build() {
    Column() {
      Stack() {
        Particle({
          particles: [
            this.createImageParticle($r("app.media.book"), 1.5, 8000),   // book particle: scale to 1.5x, lasting 8000 ms
            this.createImageParticle($r('app.media.heart'), 2.0, 10000),  // heart particle: scale to 2.0x, lasting 10000 ms
          ]
        }).width(300).height(300)

      }.width(500).height(500).align(Alignment.Center)
    }.width('100%').height('100%')

  }
}
```

### Example 3: Changing Motion Trajectories with the Particle Disturbance Field

This example demonstrates the effect of particle motion trajectory changes under the interference of a disturbance field.



```TypeScript
@Entry
@Component
struct ParticleExample3 {
  build() {
    Stack() {
      Text()
        .width(300).height(300).backgroundColor(Color.Black)
      Particle({
        particles: [
          {
            emitter: {
              particle: {
                type: ParticleType.POINT, // Particle type.
                config: {
                  radius: 10 // Dot radius.
                },
                count: 500, // Total number of particles.
                lifetime: 10000 // Particle lifecycle, in ms.
              },
              emitRate: 10, // Number of particles emitted per second.
              position: [0, 0],
              shape: ParticleEmitterShape.RECTANGLE // Emitter shape.
            },
            color: {
              range: [Color.Red, Color.Yellow], // Initial color range.
              updater: {
                type: ParticleUpdater.CURVE, // Change mode is curve.
                config: [
                  {
                    from: Color.White, // Start value of the change.
                    to: Color.Pink, // End value of the change.
                    startMillis: 0, // Start time.
                    endMillis: 3000, // End time.
                    curve: Curve.EaseIn // Change curve.
                  },
                  {
                    from: Color.Pink,
                    to: Color.Orange,
                    startMillis: 3000,
                    endMillis: 5000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: Color.Orange,
                    to: Color.Pink,
                    startMillis: 5000,
                    endMillis: 8000,
                    curve: Curve.EaseIn
                  },
                ]
              }
            },
            opacity: {
              range: [0.0, 1.0], // Initial particle opacity is randomly generated from [0.0, 1.0].
              updater: {
                type: ParticleUpdater.CURVE,
                config: [
                  {
                    from: 0.0,
                    to: 1.0,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: 1.0,
                    to: 0.0,
                    startMillis: 5000,
                    endMillis: 10000,
                    curve: Curve.EaseIn
                  }
                ]
              }
            },
            scale: {
              range: [0.0, 0.0],
              updater: {
                type: ParticleUpdater.CURVE,
                config: [
                  {
                    from: 0.0,
                    to: 0.5,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  }
                ]
              }
            },
            acceleration: {
              // Acceleration configuration, which changes in two dimensions: magnitude and direction. speed indicates the acceleration magnitude, and angle indicates the acceleration direction.
              speed: {
                range: [3, 9],
                updater: {
                  type: ParticleUpdater.RANDOM,
                  config: [1, 20]
                }
              },
              angle: {
                range: [90, 90]
              }
            }

          }
        ]
      // Set the particle disturbance field to interfere with the particle motion trajectory.
      }).width(300).height(300).disturbanceFields([{
        strength: 10, // Field strength, indicating the intensity of the repulsive or attractive force.
        shape: DisturbanceFieldShape.RECT, // Disturbance field shape is rectangle.
        size: { width: 100, height: 100 }, // Disturbance field size.
        position: { x: 100, y: 100 }, // Disturbance field position.
        feather: 15, // Feather value, indicating the degree of attenuation of the field from the center to the edge.
        noiseScale: 10, // Noise scale.
        noiseFrequency: 15, // Noise frequency.
        noiseAmplitude: 5 // Noise amplitude.
      }])
    }.width('100%').height('100%').align(Alignment.Center)
  }
}
```

### Example 4: Adjusting the Emitter Position

This example demonstrates how to adjust the position of the particle emitter through emitter().



```TypeScript
@Entry
@Component
struct ParticleExample4 {
  @State emitterProperties: Array<EmitterProperty> = [
    {
      index: 0,
      emitRate: 100,
      position: { x: 60, y: 80 },
      size: { width: 200, height: 200 }
    }
  ];

  build() {
    Stack() {
      Text()
        .width(300).height(300).backgroundColor(Color.Black)
      Particle({
        particles: [
          {
            emitter: {
              particle: {
                type: ParticleType.POINT, // Particle type.
                config: {
                  radius: 5 // Radius of the dot.
                },
                count: 400, // Total number of particles.
                lifetime: -1 // Lifecycle of the particle. -1 indicates an infinite lifecycle.
              },
              emitRate: 10, // Number of particles emitted per second.
              position: [0, 0], // Emitter position.
              shape: ParticleEmitterShape.CIRCLE // Emitter shape.
            },
            color: {
              range: [Color.Red, Color.Yellow], // Initial color range.
              updater: {
                type: ParticleUpdater.CURVE, // Change with the animation curve.
                config: [
                  {
                    from: Color.White,
                    to: Color.Pink,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: Color.Pink,
                    to: Color.Orange,
                    startMillis: 3000,
                    endMillis: 5000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: Color.Orange,
                    to: Color.Pink,
                    startMillis: 5000,
                    endMillis: 8000,
                    curve: Curve.EaseIn
                  },
                ]
              }
            },
          },
        ]
      })
        .width(300)
        .height(300)
        .emitter(this.emitterProperties)
    }.width('100%').height('100%').align(Alignment.Center)
  }
}
```

### Example 5: Creating an Annulus Emitter

This example demonstrates how to create a annulus emitter, where particles are statically emitted across the entire annulus range (from the start angle 0 to the end angle 360).



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ParticleExample5 {
  build() {
    Stack() {
      Text()
        .width(300).height(300).backgroundColor(Color.Black)
      Particle({
        particles: [
          {
            emitter: {
              particle: {
                type: ParticleType.POINT, // Particle type.
                config: {
                  radius: 5 // Dot radius.
                },
                count: 2000, // Total number of particles.
                lifetime: 10000, // Particle lifecycle, in ms.
                lifetimeRange: 100 // Value range of the particle lifecycle, in ms.
              },
              emitRate: 100, // Number of particles emitted per second.
              shape: ParticleEmitterShape.ANNULUS, // Annulus emitter.
              annulusRegion:{
                center:{x:LengthMetrics.percent(0.5),y:LengthMetrics.percent(0.5)}, // Coordinates of the center of the annulus
                innerRadius:LengthMetrics.vp(100), // Inner radius of the annulus.
                outerRadius:LengthMetrics.vp(120), // Outer radius of the annulus.
                startAngle:0, // Start angle of the annulus
                endAngle:360 // End angle of the annulus
              }
            },
            color: {
              range: [Color.Pink, Color.White],
            },
            opacity: {
              range: [0.0, 1.0],
              updater: {
                type: ParticleUpdater.CURVE,
                config: [
                  {
                    from: 0.0,
                    to: 1.0,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  },
                  {
                    from: 1.0,
                    to: 0.0,
                    startMillis: 5000,
                    endMillis: 10000,
                    curve: Curve.EaseIn
                  }
                ]
              }
            },
            scale: {
              range: [0.0, 0.0],
              updater: {
                type: ParticleUpdater.CURVE,
                config: [
                  {
                    from: 0.0,
                    to: 0.5,
                    startMillis: 0,
                    endMillis: 3000,
                    curve: Curve.EaseIn
                  }
                ]
              }
            },
          }
        ]
      }).width(300).height(300)
    }.width('100%').height('100%').align(Alignment.Center)
  }
}
```

### Example 6: Annulus Emitter Update

This example describes the basic usage of updating the annulus emitter of a particle animation.



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ParticleExample6 {
  @State radius: number = 1;
  @State shape: ParticleEmitterShape = ParticleEmitterShape.ANNULUS; // Annulus.
  @State emitRate: number = 200;
  @State count: number = 4000;
  private timerID: number = -1;
  private centerX: LengthMetrics = LengthMetrics.percent(0.5);
  private centerY: LengthMetrics = LengthMetrics.percent(0.5);
  private inRadius: LengthMetrics = LengthMetrics.vp(120);
  private outRadius: LengthMetrics = LengthMetrics.vp(120);
  private startAngle: number = -90;   // 12 o'clock direction.
  private endAngle: number = -60;   // 1 o'clock direction.

  // Set the update parameters of the annulus emitter for the particle animation.
  @State emitterProperties: Array<EmitterProperty> = [
    {
      index: 0,
      emitRate: 100,
      annulusRegion: {
        center: {x:this.centerX, y: this.centerY}, // Center coordinates of the annulus.
        outerRadius: this.outRadius, // Outer radius of the annulus
        innerRadius: this.inRadius, // Inner radius of the annulus
        startAngle: this.startAngle, // Start angle of the annulus.
        endAngle: this.endAngle // End angle of the annulus.
      }
    }
  ]

  // Set the initial parameters of the annulus emitter upon creation.
  @State region: ParticleAnnulusRegion = {
    center: {x:this.centerX, y: this.centerY},
    outerRadius: this.outRadius,
    innerRadius: this.inRadius,
    startAngle: -90,
    endAngle: -60
  }

  onPageShow(): void {
    // Create a timer (updated every second).
    this.timerID = setInterval(() => {
      this.emitterProperties = [
        {
          index: 0,
          emitRate: this.emitRate,
          annulusRegion: {
            center:{x:this.centerX, y: this.centerY},
            outerRadius: this.outRadius,
            innerRadius: this.inRadius,
            startAngle: this.startAngle,
            endAngle: this.endAngle
          }
        }
      ];
      if (this.endAngle >= 360) {
        if (this.timerID != -1) {
          clearInterval(this.timerID);
        }
        return;
      }
      // Update the angle value (30 degrees per second).
      this.startAngle += 30;
      this.endAngle += 30;
      console.info("angle: " + this.startAngle + ", " + this.endAngle);
    }, 1000);
  }

  build() {
    Column({ space: 10}) {
      Stack() {
        Text()
          .width(300).height(300).backgroundColor(Color.Black)

        Particle({
          particles: [
            {
              emitter: {
                particle: {
                  type: ParticleType.POINT, // Particle type.
                  config: {
                    radius: this.radius // Dot radius
                  },
                  count: this.count, // Total number of particles
                  lifetime: -1 // Particle lifecycle. The value -1 indicates that the particle lifecycle is infinite.
                },
                emitRate: this.emitRate, // Number of particles emitted per second
                shape: this.shape, // Emitter shape.
                annulusRegion: this.region
              },
              color: {
                range: [Color.White, Color.Pink], // Initial color range
              },
            },
          ]
        }).width('100%')
          .height('100%')
          .emitter(this.emitterProperties)
      }
      .width('100%')
      .height('100%')
      .align(Alignment.Center)
    }
  }
}
```

### Example 7: Setting Ripple Field and Velocity Field

Since API version 22, particle ripple fields and velocity fields can be set. This example demonstrates how to set a particle ripple field through the rippleFields API to produce an effect similar to ripple diffusion. The velocityFields API is used to set a particle velocity field, so that the velocity specified by the velocity field is superimposed on the original velocity of the particles.

```TypeScript
// xxx.ets
@Entry
@Component
struct ParticleExample {
  @State count: number = 1000
  @State particle: EmitterParticleOptions<ParticleType> = {
    type: ParticleType.POINT, // Particle type
    config: {
      radius: 1 // Dot radius
    },
    count: this.count, // Total number of particles
    lifetime: 9000, // Particle lifecycle, in ms
    lifetimeRange: 100 // Particle lifecycle value range, in ms
  }
  build() {
    Column() {
      Text('Fluctuation field')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
      Stack() {
        Text()
          .width(300).height(300).backgroundColor(Color.Black)
        Particle({
          particles: [
            {
              emitter: {
                particle: this.particle,
                emitRate: 10000, // Number of particles emitted per second
                position: [0, 0],
                shape: ParticleEmitterShape.RECTANGLE // Emitter shape
              },
              color: {
                range: [Color.White, Color.White], // Initial color range
              },
              scale: {
                range: [0.2, 1.5], // Initial size range
              },
              opacity : {
                range: [0.2, 0.8], // Initial opacity range
              }
            }
          ]
        }).width(300).height(300)
          .rippleFields([
            {
              amplitude: 120, // Fluctuation field amplitude
              wavelength: 500, // Wavelength of the ripple field
              waveSpeed: 220, // Wave speed of the ripple field
              center: { x: 150, y: 150 }, // Center of the force of the ripple field
              attenuation: 0, // Attenuation coefficient of the ripple field over time
              region: {
                // Influence region of the ripple field
                shape: DisturbanceFieldShape.RECT, // Shape of the influence region of the ripple field
                position: { x: 150, y: 150 }, // Center of the influence region of the ripple field
                size: { width: 300, height: 300 } // Size of the influence region of the ripple field
              }
            }
          ])
      }.width('100%').height(300).align(Alignment.Center)
      Text('Velocity field')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
      Stack() {
        Text()
          .width(300).height(300).backgroundColor(Color.Black)
        Particle({
          particles: [
            {
              emitter: {
                particle: {
                  type: ParticleType.POINT, // Particle type
                  config: {
                    radius: 2 // Dot radius
                  },
                  count: 1000, // Total number of particles
                  lifetime: 1000, // Particle lifecycle, in ms
                  lifetimeRange: 0 // Particle lifecycle value range, in ms
                },
                emitRate: 120, // Number of particles emitted per second
                position: [0, 0],
                size: [300, 300],
                shape: ParticleEmitterShape.RECTANGLE // Emitter shape
              },
              color: {
                range: [Color.White, Color.White], // Initial color range
              },
              opacity: {
                range: [1.0, 1.0],
                updater: {
                  type: ParticleUpdater.CURVE, // Opacity changes along a curve
                  config: [
                    {
                      from: 1.0,
                      to: 0.0,
                      startMillis: 0,
                      endMillis: 1000,
                      curve: Curve.EaseIn
                    }
                  ]
                }
              },
            }
          ]
        }).width(300).height(300)
          .margin({ top: 30 })
          .velocityFields([
            {
              velocity: { x: 100, y: 0 }, // Velocity value of the velocity field
              region: {
                // Influence region of the velocity field
                shape: DisturbanceFieldShape.RECT, // Shape of the influence region of the velocity field
                position: { x: 150, y: 150 }, // Center of the influence region of the velocity field
                size: { width: 200, height: 200 } // Size of the influence region of the velocity field
              }
            }
          ])
      }.width('100%').height(300).align(Alignment.Center)
    }
  }
}
```
