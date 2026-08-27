# Path2D

路径对象，支持通过对象的接口进行路径的描述，并通过Canvas的stroke接口或者fill接口进行绘制。

> **说明：**
> 
> Path2D对象不支持重置已设置的路径，如需新路径可重新创建一个空的Path2D对象。
> 
> Path2D对象的方法无法对
> [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)
> 和
> [OffscreenCanvasRenderingContext2D](arkts-arkui-offscreencanvasrenderingcontext2d-c.md)
> 对象中设置的路径生效。

**继承/实现关系：** Path2D extends [CanvasPath](arkts-arkui-canvaspath-c.md)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## addPath

```TypeScript
addPath(path: Path2D, transform?: Matrix2D): void
```

将另一个路径添加到当前的路径对象中，并使用Matrix2D对象对新添加的路径对象进行图形变换。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | 是 | 需要添加到当前路径的路径对象，路径单位：px。 异常值undefined和null按无效值处理。 |
| transform | Matrix2D | 否 | 新增路径的变换矩阵对象。 异常值undefined和null按无效值处理。 默认值：null。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct AddPath {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private path2Da: Path2D = new Path2D('M250 150 L150 350 L350 350 Z');
  private path2Db: Path2D = new Path2D();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.path2Db.addPath(this.path2Da)
          this.context.stroke(this.path2Db)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## constructor

```TypeScript
constructor()
```

构造二维变换矩阵对象，默认值是属性全为0的矩阵。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

以下示例展示了配置CanvasRenderingContext2D对象的单位模式，默认单位模式为LengthMetricsUnit.DEFAULT，对应默认单位vp，配置后无法动态更改。详细说明见LengthMetricsUnit。

```TypeScript
// xxx.ets
import { LengthMetricsUnit } from '@kit.ArkUI'

@Entry
@Component
struct LengthMetricsUnitDemo {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private contextPX: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings, LengthMetricsUnit.PX);
  private contextVP: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.contextPX)
        .width('100%')
        .height(150)
        .backgroundColor('#ffff00')
        .onReady(() => {
          // 使用px单位模式绘制图形
          this.contextPX.fillRect(10, 10, 100, 100)
          this.contextPX.clearRect(10, 10, 50, 50)
        })

      Canvas(this.contextVP)
        .width('100%')
        .height(150)
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.contextVP.fillRect(10, 10, 100, 100)
          this.contextVP.clearRect(10, 10, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

构造二维变换矩阵对象，默认值是属性全为0的矩阵，支持配置Matrix2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | LengthMetricsUnit | 是 | 用来配置Matrix2D对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](arkts-arkui-canvas-con.md) 。 默认值：DEFAULT 异常值NaN和Infinity按默认值处理。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(path: Path2D)
```

使用路径对象构造Path2D对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | 是 | 路径对象。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(path: Path2D, unit: LengthMetricsUnit)
```

使用路径对象构造Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [Path2D](arkts-arkui-path2d-c.md) | 是 | 路径对象。 |
| unit | LengthMetricsUnit | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改， 配置方法同 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)。 异常值NaN和Infinity按默认值处理。 默认值：DEFAULT。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(d: string)
```

使用符合SVG路径描述规范的路径字符串构造Path2D对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| d | string | 是 | 符合SVG路径描述规范的路径字符串，格式参考 SVG路径描述规范， 异常值按无效值处理。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(description: string, unit: LengthMetricsUnit)
```

使用符合SVG路径描述规范的路径字符串构造Path2D对象，支持配置Path2D对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string | 是 | 符合SVG路径描述规范的路径字符串，格式参考 SVG路径描述规范， 异常值按无效值处理。 |
| unit | LengthMetricsUnit | 是 | 用来配置Path2D对象的单位模式，配置后无法动态更改， 配置方法同 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)。 异常值NaN和Infinity按默认值处理。 默认值：DEFAULT。 |

**示例**

参见 [constructor](#constructor)
