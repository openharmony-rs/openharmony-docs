# UnionEffectContainer (System API)

定义UnionEffectContainer组件.

## UnionEffectContainer

```TypeScript
UnionEffectContainer(options?: UnionEffectContainerOptions)
```

创建形状融合容器组件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UnionEffectContainerOptions](arkts-arkui-unioneffectcontainer-comp-unioneffectcontaineroptions-i-sys.md) | 否 | UnionEffectContainer构造参数，用于决定收集到的后代组件形状的融合形变程度。<br>默认值：{spacing:0} |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [UnionEffectContainerOptions](arkts-arkui-unioneffectcontainer-comp-unioneffectcontaineroptions-i-sys.md) | 设置UnionEffectContainer构造参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UnionMode](arkts-arkui-unioneffectcontainer-comp-unionmode-e-sys.md) | 设置融合效果模式。 |

## 示例

### 示例1（设置融合形变效果）

该示例主要演示如何使用[UnionEffectContainer](#unioneffectcontainer)组件，通过改变spacing值或后代组件的距离，产生融合形变效果。



```TypeScript
// UnionEffectContainerPage.ets
@Entry
@Component
struct UnionEffectContainerPage {
  @State spacing: number = 0;
  @State translateY: number = 0;

  build() {
    Column() {
      Column() {
        UnionEffectContainer({ spacing: 10 }) {
          Column({ space: 50 }) {
            Column()
              .width(100)
              .height(100)
              .margin({ top: 10 })
              .borderRadius(50)
              .useUnionEffect(true) // 设置useUnionEffect属性，使用融合效果
              .translate({ y: this.translateY })

            Column()
              .width(200)
              .height(100)
              .useUnionEffect(true)
          }
          .width('100%')
        }
        .width('100%')
        .height('80%')
        .backgroundColor('#2787d9') // 设置融合效果支持的属性，如背景色

        Row({ space: 30 }) {
          Text('translate:')
          Button('+10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY += 10; // 改变后代组件的距离
              });
            })
          Button('-10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY -= 10; // 改变后代组件的距离
              });
            })
        }
        .width('100%')
        .height('20%')
      }.width('90%')
      .height('40%')
      .borderWidth(1)
      .margin({ top: 10 })

      Column() {
        UnionEffectContainer({ spacing: this.spacing }) {
          Column({ space: 50 }) {
            Column()
              .width(100)
              .height(100)
              .margin({ top: 10 })
              .borderRadius(50)
              .useUnionEffect(true) // 设置useUnionEffect属性，使用融合效果

            Column()
              .width(200)
              .height(100)
              .useUnionEffect(true)
          }
          .width('100%')
        }
        .width('100%')
        .height('80%')
        .backgroundColor('#2787d9') // 设置融合效果支持的属性，如背景色

        Row({ space: 30 }) {
          Text('spacing:')
          Button('+20')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.spacing += 20; // 改变融合形变的程度
              });
            })
          Button('-20')
            .onClick(() => {
              if (this.spacing <= 0) {
                return;
              }
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.spacing -= 20; // 改变融合形变的程度
                if (this.spacing < 0) {
                  this.spacing = 0;
                }
              });
            })
        }
        .width('100%')
        .height('20%')
      }.width('90%')
      .height('40%')
      .borderWidth(1)
      .margin({ top: 10 })
    }.width('100%')
    .height('100%')
  }
}
```

### 示例2（设置不同类型的融合形变效果）

该示例主要演示如何使用[unionMode](#unionmode)接口，通过设置不同的融合类型，产生不同的融合形变效果。

从API版本26.0.0开始，新增unionMode接口。

```TypeScript
// UnionEffectContainerPage.ets
@Entry
@Component
struct UnionEffectContainerPage {
  @State translateY1: number = 0;
  @State translateY2: number = 0;

  build() {
    Column() {
      Column() {
        Text('UnionMode.SMOOTH_UNION')
        UnionEffectContainer({ spacing: 10 }) {
          Column({ space: 50 }) {
            Column()
              .width(100)
              .height(100)
              .margin({ top: 10 })
              .borderRadius(50)
              .useUnionEffect(true) // 设置useUnionEffect属性，使用融合效果
              .translate({ y: this.translateY1 })

            Column()
              .width(200)
              .height(100)
              .useUnionEffect(true)
          }
          .width('100%')
        }
        .width('100%')
        .height('75%')
        .backgroundColor('#2787d9') // 设置融合效果支持的属性，如背景色
        .unionMode(UnionMode.SMOOTH_UNION)

        Row({ space: 30 }) {
          Text('translate:')
          Button('+10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY1 += 10; // 改变相邻组件的距离
              });
            })
          Button('-10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY1 -= 10; // 改变相邻组件的距离
              });
            })
        }
        .width('100%')
        .height('20%')
      }.width('90%')
      .height('45%')
      .borderWidth(1)
      .margin({ top: 10 })

      Column() {
        Text('UnionMode.GRAVITY_UNION')
        UnionEffectContainer({ spacing: 1000 }) {
          Column({ space: 50 }) {
            Column()
              .width(40)
              .height(40)
              .margin({ top: 10 })
              .borderRadius(20)
              .useUnionEffect(true, {gravityCenter: true, gravityIntensity: 60}) // 设置useUnionEffect属性，使用融合效果
              .translate({ y: this.translateY2 })

            Column()
              .width(200)
              .height(100)
              .useUnionEffect(true)
          }
          .width('100%')
        }
        .width('100%')
        .height('75%')
        .backgroundColor('#2787d9') // 设置融合效果支持的属性，如背景色
        .unionMode(UnionMode.GRAVITY_UNION)

        Row({ space: 30 }) {
          Text('translate:')
          Button('+10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY2 += 10; // 改变相邻组件的距离
              });
            })
          Button('-10')
            .onClick(() => {
              this.getUIContext().animateTo({ duration: 200 }, () => {
                this.translateY2 -= 10; // 改变相邻组件的距离
              });
            })
        }
        .width('100%')
        .height('20%')
      }.width('90%')
      .height('45%')
      .borderWidth(1)
      .margin({ top: 10 })
    }.width('100%')
    .height('100%')
  }
}
```
