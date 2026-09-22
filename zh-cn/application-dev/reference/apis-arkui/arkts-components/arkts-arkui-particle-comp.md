# Particle

定义Particle组件。

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

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| particles | [Particles](arkts-arkui-particle-comp-particles-i.md)&lt;PARTICLE, COLOR_UPDATER, OPACITY_UPDATER, SCALE_UPDATER, ACC_SPEED_UPDATER, ACC_ANGLE_UPDATER, SPIN_UPDATER&gt; | 是 | Array of particles. |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccelerationOptions](arkts-arkui-particle-comp-accelerationoptions-i.md) | 粒子加速度配置。 |
| [DisturbanceFieldOptions](arkts-arkui-particle-comp-disturbancefieldoptions-i.md) | 设置粒子扰动场参数。 |
| [EmitterOptions](arkts-arkui-particle-comp-emitteroptions-i.md) | 粒子发射器的配置。 |
| [EmitterParticleOptions](arkts-arkui-particle-comp-emitterparticleoptions-i.md) | 粒子配置。 |
| [EmitterProperty](arkts-arkui-particle-comp-emitterproperty-i.md) | 设置发射器属性。 |
| [FieldRegion](arkts-arkui-particle-comp-fieldregion-i.md) | 用于设置粒子场的区域信息。 |
| [ImageParticleParameters](arkts-arkui-particle-comp-imageparticleparameters-i.md) | 设置图片选项。 |
| [ParticleAnnulusRegion](arkts-arkui-particle-comp-particleannulusregion-i.md) | 用于设置环形发射器区域的配置信息。 |
| [ParticleColorOptions](arkts-arkui-particle-comp-particlecoloroptions-i.md) | 颜色变化方式为随机变化的时候，在区间内随机生成一个差值。r、g、b、a四个颜色通道每秒分别使用差值叠加当前颜色值，生成目标颜色值。实现颜色随机变化的效果。 |
| [ParticleColorPropertyOptions](arkts-arkui-particle-comp-particlecolorpropertyoptions-i.md) | 设置粒子颜色属性更新器配置。 |
| [ParticleColorPropertyUpdaterConfigs](arkts-arkui-particle-comp-particlecolorpropertyupdaterconfigs-i.md) | 设置粒子颜色属性更新器的配置。 |
| [ParticleColorUpdaterOptions](arkts-arkui-particle-comp-particlecolorupdateroptions-i.md) | 颜色属性变化配置。 |
| [ParticleConfigs](arkts-arkui-particle-comp-particleconfigs-i.md) | 设置粒子配置项。 |
| [ParticleOptions](arkts-arkui-particle-comp-particleoptions-i.md) | 设置粒子参数。 |
| [ParticlePropertyAnimation](arkts-arkui-particle-comp-particlepropertyanimation-i.md) | 设置粒子属性生命周期。 |
| [ParticlePropertyOptions](arkts-arkui-particle-comp-particlepropertyoptions-i.md) | 设置粒子属性选项。 |
| [ParticlePropertyUpdaterConfigs](arkts-arkui-particle-comp-particlepropertyupdaterconfigs-i.md) | 设置粒子属性更新器配置。 |
| [Particles](arkts-arkui-particle-comp-particles-i.md) | 粒子动画的集合。 |
| [ParticleUpdaterOptions](arkts-arkui-particle-comp-particleupdateroptions-i.md) | 属性变化配置。 |
| [PointParticleParameters](arkts-arkui-particle-comp-pointparticleparameters-i.md) | 设置粒子半径。 |
| [RippleFieldOptions](arkts-arkui-particle-comp-ripplefieldoptions-i.md) | 用于描述粒子波动场信息的参数。 |
| [VelocityFieldOptions](arkts-arkui-particle-comp-velocityfieldoptions-i.md) | 用于描述粒子速度场信息的参数。 |
| [VelocityOptions](arkts-arkui-particle-comp-velocityoptions-i.md) | 粒子速度配置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md) | 粒子元组，表示定义动画参数配置值对的类型。 |
| [PositionT](arkts-arkui-particle-comp-positiont-t.md) | 用于设置或返回组件的位置。 |
| [SizeT](arkts-arkui-particle-comp-sizet-t.md) | 定义Size类型。 |
| [Vector2T](arkts-arkui-particle-comp-vector2t-t.md) | 定义Vector2T类型。其中Vector2T类型包含x和y两个属性值。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DistributionType](arkts-arkui-particle-comp-distributiontype-e.md) | 初始颜色随机值分布类型。 |
| [DisturbanceFieldShape](arkts-arkui-particle-comp-disturbancefieldshape-e.md) | 扰动场形状。 |
| [ParticleEmitterShape](arkts-arkui-particle-comp-particleemittershape-e.md) | 粒子发射器形状。 |
| [ParticleType](arkts-arkui-particle-comp-particletype-e.md) | 粒子类型。 |
| [ParticleUpdater](arkts-arkui-particle-comp-particleupdater-e.md) | 粒子变化类型。 |

## 示例

### 示例1（圆形初始化粒子）

描述粒子动画基础用法，通过圆形初始化粒子。



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
                type: ParticleType.POINT, // 粒子类型
                config: {
                  radius: 10 // 圆点半径
                },
                count: 500, // 粒子总数
                lifetime: 10000, // 粒子生命周期，单位ms
                lifetimeRange: 100 // 粒子生命周期取值范围，单位ms
              },
              emitRate: 10, // 每秒发射粒子数
              position: [0, 0],
              shape: ParticleEmitterShape.RECTANGLE // 发射器形状
            },
            color: {
              range: [Color.Red, Color.Yellow], // 初始颜色范围
              distributionType: DistributionType.GAUSSIAN, // 初始颜色随机值分布
              updater: {
                type: ParticleUpdater.CURVE, // 变化方式为曲线变化
                config: [
                  {
                    from: Color.White, // 变化起始值
                    to: Color.Pink, // 变化终点值
                    startMillis: 0, // 开始时间
                    endMillis: 3000, // 结束时间
                    curve: Curve.EaseIn // 变化曲线
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
              range: [0.0, 1.0], // 粒子透明度的初始值从【0.0到1.0】随机产生
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
              // 加速度的配置，从大小和方向两个维度变化，speed表示加速度大小，angle表示加速度方向
              speed: {
                range: [3, 9],
                updater: {
                  type: ParticleUpdater.RANDOM, // Speed的变化方式是随机均匀变化
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

### 示例2（图片初始化粒子）

描述粒子动画基础用法，通过图片初始化粒子。该示例同时配置两种不同的图片粒子，展示多粒子类型组合效果。



```TypeScript
@Entry
@Component
struct ParticleExample {
  @State
  myCount: number = 100

  // 通过参数化配置减少重复代码，imageSrc为图片资源，scaleTo为缩放目标值，durationMs为动画持续时长
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
            this.createImageParticle($r("app.media.book"), 1.5, 8000),   // book粒子：缩放至1.5倍，持续8000ms
            this.createImageParticle($r('app.media.heart'), 2.0, 10000),  // heart粒子：缩放至2.0倍，持续10000ms
          ]
        }).width(300).height(300)

      }.width(500).height(500).align(Alignment.Center)
    }.width('100%').height('100%')

  }
}
```

### 示例3（粒子扰动场的干扰下运动轨迹发生变化）

演示粒子在扰动场干扰下运动轨迹变化的效果。



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
                type: ParticleType.POINT, // 粒子类型
                config: {
                  radius: 10 // 圆点半径
                },
                count: 500, // 粒子总数
                lifetime: 10000 // 粒子生命周期，单位ms
              },
              emitRate: 10, // 每秒发射粒子数
              position: [0, 0],
              shape: ParticleEmitterShape.RECTANGLE // 发射器形状
            },
            color: {
              range: [Color.Red, Color.Yellow], // 初始颜色范围
              updater: {
                type: ParticleUpdater.CURVE, // 变化方式为曲线变化
                config: [
                  {
                    from: Color.White, // 变化起始值
                    to: Color.Pink, // 变化终点值
                    startMillis: 0, // 开始时间
                    endMillis: 3000, // 结束时间
                    curve: Curve.EaseIn // 变化曲线
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
              range: [0.0, 1.0], // 粒子透明度的初始值从[0.0,1.0]随机产生
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
              // 加速度的配置，从大小和方向两个维度变化，speed表示加速度大小，angle表示加速度方向
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
      // 设置粒子扰动场，干扰粒子运动轨迹
      }).width(300).height(300).disturbanceFields([{
        strength: 10, // 场强，表示排斥力或吸引力的强度
        shape: DisturbanceFieldShape.RECT, // 扰动场形状为矩形
        size: { width: 100, height: 100 }, // 扰动场大小
        position: { x: 100, y: 100 }, // 扰动场位置
        feather: 15, // 羽化值，表示场从中心点到场边缘的衰减程度
        noiseScale: 10, // 噪声尺度
        noiseFrequency: 15, // 噪声频率
        noiseAmplitude: 5 // 噪声振幅
      }])
    }.width('100%').height('100%').align(Alignment.Center)
  }
}
```

### 示例4（调整粒子发射器位置）

通过emitter()调整粒子发射器的位置。



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
                type: ParticleType.POINT, // 粒子类型
                config: {
                  radius: 5 // 圆点半径
                },
                count: 400, // 粒子总数
                lifetime: -1 // 粒子的生命周期，-1表示粒子生命周期无限大
              },
              emitRate: 10, // 每秒发射粒子数
              position: [0, 0], // 粒子发射位置
              shape: ParticleEmitterShape.CIRCLE // 发射器形状
            },
            color: {
              range: [Color.Red, Color.Yellow], // 初始颜色范围
              updater: {
                type: ParticleUpdater.CURVE, // 变化方式为曲线变化
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

### 示例5（环形发射器创建）

该示例演示如何创建环形发射器，粒子在整个圆环范围内（起始角度0到结束角度360）静态发射。



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
                type: ParticleType.POINT, // 粒子类型
                config: {
                  radius: 5 // 圆点半径
                },
                count: 2000, // 粒子总数
                lifetime: 10000, // 粒子生命周期，单位ms
                lifetimeRange: 100 // 粒子生命周期取值范围，单位ms
              },
              emitRate: 100, // 每秒发射粒子数
              shape: ParticleEmitterShape.ANNULUS, // 环形发射器
              annulusRegion:{
                center:{x:LengthMetrics.percent(0.5),y:LengthMetrics.percent(0.5)}, // 圆环的圆心坐标
                innerRadius:LengthMetrics.vp(100), // 圆环的内圆半径
                outerRadius:LengthMetrics.vp(120), // 圆环的外圆半径
                startAngle:0, // 圆环的起始角度
                endAngle:360 // 圆环的结束角度
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

### 示例6（环形发射器更新）

描述粒子动画环形发射器更新的基础用法。



```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ParticleExample6 {
  @State radius: number = 1;
  @State shape: ParticleEmitterShape = ParticleEmitterShape.ANNULUS; // 圆环
  @State emitRate: number = 200;
  @State count: number = 4000;
  private timerID: number = -1;
  private centerX: LengthMetrics = LengthMetrics.percent(0.5);
  private centerY: LengthMetrics = LengthMetrics.percent(0.5);
  private inRadius: LengthMetrics = LengthMetrics.vp(120);
  private outRadius: LengthMetrics = LengthMetrics.vp(120);
  private startAngle: number = -90;   // 时钟12点钟方向
  private endAngle: number = -60;   // 时钟1点钟方向

  // 粒子动画，环形发射器的更新参数设置
  @State emitterProperties: Array<EmitterProperty> = [
    {
      index: 0,
      emitRate: 100,
      annulusRegion: {
        center: {x:this.centerX, y: this.centerY}, // 圆环的圆心坐标
        outerRadius: this.outRadius, // 圆环的外圆半径
        innerRadius: this.inRadius, // 圆环的内圆半径
        startAngle: this.startAngle, // 圆环的起始角度
        endAngle: this.endAngle // 圆环的结束角度
      }
    }
  ]

  // 创建的时候，环形发射器的初始设置
  @State region: ParticleAnnulusRegion = {
    center: {x:this.centerX, y: this.centerY},
    outerRadius: this.outRadius,
    innerRadius: this.inRadius,
    startAngle: -90,
    endAngle: -60
  }

  onPageShow(): void {
    // 创建定时器（每秒更新）
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
      // 更新角度值（30度/秒）
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
                  type: ParticleType.POINT, // 粒子类型
                  config: {
                    radius: this.radius // 圆点半径
                  },
                  count: this.count, // 粒子总数
                  lifetime: -1 // 粒子的生命周期，-1表示粒子生命周期无限大
                },
                emitRate: this.emitRate, // 每秒发射粒子数
                shape: this.shape, // 发射器形状
                annulusRegion: this.region
              },
              color: {
                range: [Color.White, Color.Pink], // 初始颜色范围
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

### 示例7（设置波动场和速度场）

从API version 22开始，支持设置粒子波动场和速度场。该示例演示如何通过rippleFields接口设置粒子波动场，产生类似波纹扩散的效果。通过velocityFields接口设置粒子速度场，使粒子在原有速度的基础上叠加速度场指定的速度。

```TypeScript
// xxx.ets
@Entry
@Component
struct ParticleExample {
  @State count: number = 1000
  @State particle: EmitterParticleOptions<ParticleType> = {
    type: ParticleType.POINT, // 粒子类型
    config: {
      radius: 1 // 圆点半径
    },
    count: this.count, // 粒子总数
    lifetime: 9000, // 粒子生命周期，单位ms
    lifetimeRange: 100 // 粒子生命周期取值范围，单位ms
  }
  build() {
    Column() {
      Text('波动场')
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
                emitRate: 10000, // 每秒发射粒子数
                position: [0, 0],
                shape: ParticleEmitterShape.RECTANGLE // 发射器形状
              },
              color: {
                range: [Color.White, Color.White], // 初始颜色范围
              },
              scale: {
                range: [0.2, 1.5], // 初始大小范围
              },
              opacity : {
                range: [0.2, 0.8], // 初始透明度范围
              }
            }
          ]
        }).width(300).height(300)
          .rippleFields([
            {
              amplitude: 120, // 波动场幅值
              wavelength: 500, // 波动场的波长
              waveSpeed: 220, // 波动场的波速
              center: { x: 150, y: 150 }, // 波动场的力的中心
              attenuation: 0, // 波动场随时间的衰减系数
              region: {
                // 波动场的影响区域
                shape: DisturbanceFieldShape.RECT, // 波动场影响区域的形状
                position: { x: 150, y: 150 }, // 波动场影响区域的区域中心
                size: { width: 300, height: 300 } // 波动场影响区域的大小
              }
            }
          ])
      }.width('100%').height(300).align(Alignment.Center)
      Text('速度场')
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
                  type: ParticleType.POINT, // 粒子类型
                  config: {
                    radius: 2 // 圆点半径
                  },
                  count: 1000, // 粒子总数
                  lifetime: 1000, // 粒子生命周期，单位ms
                  lifetimeRange: 0 // 粒子生命周期取值范围，单位ms
                },
                emitRate: 120, // 每秒发射粒子数
                position: [0, 0],
                size: [300, 300],
                shape: ParticleEmitterShape.RECTANGLE // 发射器形状
              },
              color: {
                range: [Color.White, Color.White], // 初始颜色范围
              },
              opacity: {
                range: [1.0, 1.0],
                updater: {
                  type: ParticleUpdater.CURVE, // 透明度按曲线变化
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
              velocity: { x: 100, y: 0 }, // 速度场的速度值
              region: {
                // 速度场的影响区域
                shape: DisturbanceFieldShape.RECT, // 速度场影响区域的形状
                position: { x: 150, y: 150 }, // 速度场影响区域的区域中心
                size: { width: 200, height: 200 } // 速度场影响区域的大小
              }
            }
          ])
      }.width('100%').height(300).align(Alignment.Center)
    }
  }
}
```
