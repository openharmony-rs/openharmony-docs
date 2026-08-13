# Circle

用于绘制圆形的组件。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 无

## Circle

```TypeScript
Circle(value?: CircleOptions)
```

use new function to set the value.

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CircleInterface-new (value?: CircleOptions): CircleAttribute--><!--Device-CircleInterface-new (value?: CircleOptions): CircleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CircleOptions](arkts-arkui-circleoptions-i.md) | 否 |  |

## Circle

```TypeScript
Circle(value?: CircleOptions)
```

用于绘制圆形的构造函数。调用后创建一个Circle对象，可设置宽高属性。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CircleInterface-(value?: CircleOptions): CircleAttribute--><!--Device-CircleInterface-(value?: CircleOptions): CircleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CircleOptions](arkts-arkui-circleoptions-i.md) | 否 | 设置圆形尺寸。当需要自定义圆形大小时传入此参数，不传入时width和height默认为0。 <br>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [CircleOptions](arkts-arkui-circleoptions-i.md)
