# Rect

矩形绘制组件，用于在界面中绘制矩形图形，支持设置填充颜色、边框样式、圆角等属性。
> **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 该组件从API version 20开始支持使用AttributeUpdater类的 > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

Use new function to create Rect. Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) \| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 否 | Rect options |

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

用于绘制矩形的构造函数。调用后创建一个Rect对象，可设置宽度、高度、圆角等属性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) \| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 否 | Rect绘制属性，包含宽度、高度、圆角等配置。不传入时使用各属性默认值绘制矩形（宽高和圆角均为0）。  异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RectOptions](arkts-arkui-rectoptions-i.md) | 用于描述矩形绘制组件的绘制属性。 |
| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 用于描述圆角矩形绘制组件的绘制属性。 |

## 示例

使用fill、fillOpacity、stroke、radius属性分别绘制矩形的填充颜色、透明度、边框颜色、圆角。

```TypeScript
// xxx.ets
@Entry
@Component
struct RectExample {
  build() {
    Column({ space: 10 }) {
      Text('normal').fontSize(11).fontColor(0xCCCCCC).width('90%')
      // 绘制90% * 50的矩形
      Column({ space: 5 }) {
        Text('normal').fontSize(9).fontColor(0xCCCCCC).width('90%')
        // 绘制90% * 50矩形
        Rect({ width: '90%', height: 50 })
          .fill(Color.Pink)
        // 绘制90% * 50的矩形框
        Rect()
          .width('90%')
          .height(50)
          .fillOpacity(0)
          .stroke(Color.Red)
          .strokeWidth(3)

        Text('with rounded corners').fontSize(11).fontColor(0xCCCCCC).width('90%')
        // 绘制90% * 80的矩形, 圆角宽高分别为40、20
        Rect({ width: '90%', height: 80 })
          .radiusHeight(20)
          .radiusWidth(40)
          .fill(Color.Pink)
        // 绘制90% * 80的矩形, 圆角宽高为20
        Rect({ width: '90%', height: 80 })
          .radius(20)
          .fill(Color.Pink)
          .stroke(Color.Transparent)
      }.width('100%').margin({ top: 10 })

      // 绘制90% * 80矩形, 左上圆角宽高40,右上圆角宽高20,右下圆角宽高40,左下圆角宽高20
      Rect({ width: '90%', height: 80 })
        .radius([[40, 40], [20, 20], [40, 40], [20, 20]])
        .fill(Color.Pink)
    }.width('100%').margin({ top: 5 })
  }
}
```

从API version 18开始，新增linearGradient、clipShape通用属性。

```TypeScript
// xxx.ets
@Entry
@Component
struct RectExample {
  build() {
    Column({ space: 10 }) {
      Column()
        .width(100)
        .height(100)
        .linearGradient({
          direction: GradientDirection.Right,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 1.0]]
        })
        .clipShape(new Rect({ width: 100, height: 100, radius: 40 }))
      Rect()
        .width(100)
        .height(100)
        // 设置矩形填充，如果需要显示背景的渐变色，请设置区域透明度.fillOpacity(0.0)
        .fill(Color.Pink)
        // 设置圆角为40
        .radius(40)
        .stroke(Color.Black)
        // 设置渐变色，仅100*100的矩形区域生效，渐变色的边界不包含倒角
        .linearGradient({
          direction: GradientDirection.Right,
          colors: [[0xff0000, 0.0], [0x0000ff, 0.3], [0xffff00, 1.0]]
        })
    }
  }
}
```

width、height、radius、radiusWidth、radiusHeight等属性分别使用不同的长度类型绘制图形。

```TypeScript
// xxx.ets
@Entry
@Component
struct RectExample {
  build() {
    Column({ space: 10 }) {
      // 绘制90% * 50矩形，圆角半径为5
      Rect({ width: '90%', height: '50', radius: '5' }) // 使用string类型
        .fill(Color.Green)
      // 绘制200 * 50的矩形框，圆角半径为5
      Rect({ width: 200, height: 50, radius: 5 }) // 使用number类型
        .fillOpacity(0)
        .stroke(Color.Red)
        .strokeWidth(3)
      // 使用Resource类型从资源文件获取尺寸和圆角参数绘制矩形
      Rect({
        width: $r('app.string.RectWidth'), // 使用Resource类型，需用户自定义
        height: $r('app.string.RectHeight'),
        radius: $r('app.string.RectRadius')
      })
        .radiusWidth($r('app.string.RectRadiusWidth'))
        .radiusHeight($r('app.string.RectRadiusHeight'))
        .fill(Color.Green)
    }.width('100%').margin({ top: 5 })
  }
}
```

以下示例展示了如何使用attributeModifier动态设置Rect组件的fill、fillOpacity、stroke、strokeDashArray、strokeDashOffset、strokeLineCap、strokeLineJoin、strokeMiterLimit、strokeOpacity、strokeWidth和antiAlias属性。

```TypeScript
// xxx.ets
class MyRectModifier implements AttributeModifier<RectAttribute> {
  applyNormalAttribute(instance: RectAttribute): void {
    // 填充颜色#707070，填充透明度0.5，边框颜色#2787D9，边框线段长度和间隙长度均为20，向左偏移15，线条两端样式为半圆，拐角样式使用尖角连接路径段，斜接长度与边框宽度比值的极限值为5，边框透明度0.5，边框宽度10，抗锯齿开启
    instance.fill("#707070")
    instance.fillOpacity(0.5)
    instance.stroke("#2787D9")
    instance.strokeDashArray([20])
    instance.strokeDashOffset("15")
    instance.strokeLineCap(LineCapStyle.Round)
    instance.strokeLineJoin(LineJoinStyle.Miter)
    instance.strokeMiterLimit(5)
    instance.strokeOpacity(0.5)
    instance.strokeWidth(10)
    instance.antiAlias(true)
  }
}

@Entry
@Component
struct RectModifierDemo {
  @State modifier: MyRectModifier = new MyRectModifier()

  build() {
    Column() {
      Rect()
        .width(200)
        .height(200)
        .attributeModifier(this.modifier)
        .offset({ x: 20, y: 20 })
    }
  }
}
```
