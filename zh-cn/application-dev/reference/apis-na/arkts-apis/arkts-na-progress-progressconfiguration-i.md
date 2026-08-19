# ProgressConfiguration

进度条配置。继承自CommonConfiguration。

**继承/实现关系：** ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ProgressConfiguration--><!--Device-unnamed-export declare interface ProgressConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total: double
```

进度总长。 默认值：100 **说明：** total是负数时，按照100处理。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressConfiguration-value: double--><!--Device-ProgressConfiguration-value: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

