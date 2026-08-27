# LengthMetrics

用于设置长度属性，当长度单位为PERCENT时，值为1表示100%。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): LengthMetrics
```

设置LengthMetrics对象是否跟随系统配置变化自动更新。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 使用[resource](#resource)方法构造的LengthMetrics对象是否在系统配置变化时自动刷新值。 true表示主动监听系统配置变化，在变化时值刷新为对应配置下的资源值。 false表示不主动监听系统配置变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 返回设置自动刷新属性后的LengthMetrics对象。 |

**示例**

```TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct MyStateSample {
  @State lengthMetrics: LengthMetrics = LengthMetrics.resource($r('sys.float.ohos_id_button_min_width')).autoRefresh!(true);

  build() {
    Column() {
      Button('Test LengthMetrics')
        .padding({ top: this.lengthMetrics })
    }
  }
}
```

## constructor

```TypeScript
constructor(value: number, unit?:LengthUnit)
```

LengthMetrics的构造函数。若参数unit不传入值或传入undefined，返回值使用默认单位VP；若unit传入非LengthUnit类型的值，返回默认值0VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。 取值范围：(-∞, +∞) |
| unit | [LengthUnit](arkts-arkui-graphics-lengthunit-e.md) | 否 | 长度属性的单位，默认为VP。 |

## fp

```TypeScript
static fp(value: number): LengthMetrics
```

用于生成单位为FP的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。 取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 单位为FP的长度属性对象。 |

## lpx

```TypeScript
static lpx(value: number): LengthMetrics
```

用于生成单位为LPX的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。 取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 单位为LPX的长度属性对象。 |

## percent

```TypeScript
static percent(value: number): LengthMetrics
```

用于生成单位为PERCENT的长度属性，值为1表示100%。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。 取值范围：[0, 1] 超出范围时按边界值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 单位为PERCENT的长度属性对象，值为1表示100%。 |

## px

```TypeScript
static px(value: number): LengthMetrics
```

用于生成单位为PX的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。 取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 单位为PX的长度属性对象。 |

## resource

```TypeScript
static resource(value: Resource): LengthMetrics
```

用于生成Resource类型资源的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 长度属性的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | Resource类型资源的长度属性对象。 |

**示例**

使用LengthMetrics设置Row的padding和margin属性。

```TypeScript
import { LengthMetrics, LengthUnit } from '@kit.ArkUI';

@Entry
@Component
struct SizeExample {
  build() {
    Column({ space: 10 }) {
      Text('margin and padding:')
        .fontSize(12)
        .fontColor(0xCCCCCC)
        .width('90%')
      Row() {
        Row() {
          Row()
            .size({ width: '100%', height: '100%' })
            .backgroundColor('#ffd5d5d5')
        }
        .width(80)
        .height(80)
        .padding({
          top: new LengthMetrics(20, LengthUnit.VP),
          bottom: LengthMetrics.px(15),
          start: LengthMetrics.vp(10),
          end: LengthMetrics.fp(20)
        })
        .margin({
          top: LengthMetrics.percent(0.1),
          bottom: LengthMetrics.lpx(20),
          start: LengthMetrics.resource($r('app.float.row_margin_start')),
          end: LengthMetrics.vp(10)
        })
        .backgroundColor(Color.White)
      }
      .backgroundColor('#ff2787d9')
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```

## vp

```TypeScript
static vp(value: number): LengthMetrics
```

用于生成单位为VP的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。 取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 单位为VP的长度属性对象。 |

## unit

```TypeScript
public unit: LengthUnit
```

长度属性的单位，默认为VP。

**类型：** [LengthUnit](arkts-arkui-graphics-lengthunit-e.md)

**默认值：** VP

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: number
```

长度属性的值。取值范围：(-∞, +∞)。当unit为PERCENT时，value表示百分比（1表示100%），参考尺寸取决于具体使用场景；其余单位表示对应单位的绝对长度。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
