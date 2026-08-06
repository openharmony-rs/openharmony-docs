# ProgressConfiguration

进度条配置。继承自[CommonConfiguration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** ProgressConfiguration extends [CommonConfiguration<ProgressConfiguration>](CommonConfiguration<ProgressConfiguration>)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>--><!--Device-unnamed-export declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total: double
```

进度总长。 默认值：100 **说明：** total是负数时，按照100处理。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressConfiguration-total: double--><!--Device-ProgressConfiguration-total: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: double
```

当前进度值。当设置的数值小于0时，将其置为0。当设置的数值大于total时，将其置为total。 默认值：0 取值范围：[0, total]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressConfiguration-value: double--><!--Device-ProgressConfiguration-value: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

