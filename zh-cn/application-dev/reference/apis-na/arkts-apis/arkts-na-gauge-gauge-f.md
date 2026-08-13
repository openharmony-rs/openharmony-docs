# Gauge

## Gauge

```TypeScript
@ComponentBuilder
export declare function Gauge(
    options: GaugeOptions, 
    content_?: CustomBuilder
): GaugeAttribute
```

创建数据量规图表组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Gauge(    options: GaugeOptions,     content_?: CustomBuilder): GaugeAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Gauge(    options: GaugeOptions,     content_?: CustomBuilder): GaugeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GaugeOptions](arkts-na-gauge-gaugeoptions-i.md) | 是 | 数据量规图表组件参数。 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GaugeAttribute |  |


## Gauge

```TypeScript
@Builder
export declare function Gauge(
    style: CustomBuilderT<GaugeAttribute>,
    content_?: CustomBuilder,
): GaugeAttribute
```

定义Gauge组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Gauge(    style: CustomBuilderT<GaugeAttribute>,    content_?: CustomBuilder,): GaugeAttribute--><!--Device-unnamed-@Builderexport declare function Gauge(    style: CustomBuilderT<GaugeAttribute>,    content_?: CustomBuilder,): GaugeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;GaugeAttribute&gt; | 是 | Gauge属性的实例。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GaugeAttribute |  |

