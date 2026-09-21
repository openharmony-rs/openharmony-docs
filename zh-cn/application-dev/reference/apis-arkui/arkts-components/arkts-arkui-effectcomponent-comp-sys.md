# EffectComponent (System API)

特效合并容器组件，用于子节点特效绘制的合并，实现特效的绘制性能优化。

> **说明：** > > - 该组件从API Version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。 > > - 本模块为系统接口。

> - 目前该组件仅支持子组件背景模糊效果的绘制合并优化。 > > - 在对子组件的背景模糊特效进行绘制合并时，需要将子组件的backgroundBlurStyle(BlurStyle)属性替换成useEffect(true)。

## 子组件

可以包含子组件。

## EffectComponent

```TypeScript
EffectComponent()
```

创建特效绘制合并组件，用于对子组件背景模糊特效的绘制合并。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## EffectComponent

```TypeScript
EffectComponent(options?: EffectComponentOptions)
```

创建特效绘制合并组件，无参数或者参数为EffectLayer.None时用于对子组件背景模糊特效的绘制合并。有明确参数时表示当前渲染图层置于特殊图层。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EffectComponentOptions](arkts-arkui-effectcomponent-comp-effectcomponentoptions-i-sys.md) | 否 | EffectComponent构造参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [EffectComponentOptions](arkts-arkui-effectcomponent-comp-effectcomponentoptions-i-sys.md) | 设置当前EffectComponent构造参数，包含EffectComponent的渲染层级。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EffectLayer](arkts-arkui-effectcomponent-comp-effectlayer-e-sys.md) | EffectComponent的渲染层级。 |

## 示例

### 示例1（使用特效绘制合并能力）

该示例主要演示如何使用特效绘制合并组件。



```TypeScript
//Index.ets
@Entry
@Component
struct Index {
  build() {
    Stack() {
      Image($r("app.media.example"))
        .autoResize(true)
      EffectComponent() {
        Column({ space: 20 }) {
          // 使用backgroundBlurStyle进行模糊绘制
          Text("Normal text with backgroundBlurStyle")
            .textAlign(TextAlign.Center)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .backgroundBlurStyle(BlurStyle.Thick)
            .borderRadius(16)
            .width('90%')
            .height('48')

          // 不进行模糊绘制
          Text("Normal text without blur effect")
            .textAlign(TextAlign.Center)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .border({ width: 1 })
            .borderRadius(16)
            .width('90%')
            .height('48')

          // 使用useEffect进行模糊合并绘制，继承EffectComponent的模糊参数
          Text("Normal text with useEffect blur 1")
            .textAlign(TextAlign.Center)
            .useEffect(true)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .borderRadius(16)
            .width('90%')
            .height('48')

          // 使用useEffect进行模糊合并绘制，继承EffectComponent的模糊参数
          Text("Normal text with useEffect blur 2")
            .textAlign(TextAlign.Center)
            .useEffect(true)
            .fontSize(16)
            .fontWeight(FontWeight.Medium)
            .borderRadius(16)
            .width('90%')
            .height('48')
        }
        .width('100%')
      }
      .backgroundBlurStyle(BlurStyle.Thin)
    }
    .backgroundColor(Color.Black)
    .width('100%')
    .height('100%')
  }
}
```

### 示例2（独立渲染图层）

该示例主要演示如何渲染充电文字层。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Stack() {
      Image($r("app.media.startIcon"))
        .autoResize(true)
      EffectComponent({effectLayer: EffectLayer.CHARGE_TEXT}) {
        Text('CHARGE_TEXT')
          .height('50%')
          .width('100%')
          .fontSize(50)
          .textAlign(TextAlign.Center);
      }
      .backgroundBlurStyle(BlurStyle.Thin)
    }
    .backgroundColor(Color.Black)
    .width('100%')
    .height('100%')
  }
}
```
