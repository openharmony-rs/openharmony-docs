# Polyline

折线绘制组件。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 该组件从API version 20开始支持使用AttributeUpdater类的 > updateConstructorParams接口更新构造参数。

## 子组件 无

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

Uses new to create Polyline. Anonymous Object Rectification.

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolylineInterface-new (options?: PolylineOptions): PolylineAttribute--><!--Device-PolylineInterface-new (options?: PolylineOptions): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | 否 | Poly line options |

## Polyline

```TypeScript
Polyline(options?: PolylineOptions)
```

用于绘制折线的构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolylineInterface-(options?: PolylineOptions): PolylineAttribute--><!--Device-PolylineInterface-(options?: PolylineOptions): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polylineoptions-i.md) | 否 | Polyline绘制区域，用于设置Polyline组件的宽度和高度。当需要指定Polyline的绘制区域大小时传入此参数，不传入时使用默认宽度和高度（均 为0）。 <br>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [PolylineOptions](arkts-arkui-polylineoptions-i.md)
