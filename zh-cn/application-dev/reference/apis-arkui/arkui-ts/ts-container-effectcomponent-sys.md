# EffectComponent (系统接口)

特效合并容器组件，用于子节点特效绘制的合并，实现特效的绘制性能优化。

>  **说明：**
>
> - 该组件从API Version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块为系统接口。
>
> - 目前该组件仅支持子组件背景模糊效果的绘制合并优化。
>
> - 在对子组件的背景模糊特效进行绘制合并时，需要将子组件的backgroundBlurStyle(BlurStyle)属性替换成useEffect(true)。


## 子组件

可以包含子组件。

## 接口

### EffectComponent

EffectComponent()

创建特效绘制合并组件，用于对子组件背景模糊特效的绘制合并。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### EffectComponent<sup>20+</sup>

EffectComponent(options?: EffectComponentOptions)

创建特效绘制合并组件，无参数或者参数为EffectLayer.None时用于对子组件背景模糊特效的绘制合并。有明确参数时表示当前渲染图层置于特殊图层。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名            | 类型        | 必填   | 说明                                     |
| -------------- | ---------------------------------------- | ---- |  ---------------------------------------- |
| options      | [EffectComponentOptions](#effectcomponentoptions20对象说明) | 否    |  EffectComponent构造参数。               |

## 事件

不支持通用事件。

## 属性

支持通用属性，目前仅支持对backgroundBlurStyle属性做绘制合并优化。

## EffectComponentOptions<sup>20+</sup>对象说明

设置当前EffectComponent构造参数，包含EffectComponent的渲染层级。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称        | 类型                                    | 必填 | 说明                                                     |
| ----------- | --------------------------------------- | ---- | -------------------------------------------------------- |
| effectLayer | [EffectLayer](#effectlayer20枚举说明) | 否   | EffectComponent的渲染层级。<br/>默认值：EffectLayer.NONE |

## EffectLayer<sup>20+</sup>枚举说明

EffectComponent的渲染层级。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 值   | 说明         |
| :------------ | :--- | :----------- |
| NONE          | 0    | 无特效层。   |
| CHARGE_MOTION | 1    | 充电动画层。 |
| CHARGE_TEXT   | 2    | 充电文字层。 |

## 示例

### 示例1（使用特效绘制合并能力）

该示例主要演示如何使用特效绘制合并组件。

```ts
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

![zh-cn_image_effectcomponent](figures/zh-cn_image_effectcomponent.png)

### 示例2（独立渲染图层）

该示例主要演示如何渲染充电文字层。

```ts
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

