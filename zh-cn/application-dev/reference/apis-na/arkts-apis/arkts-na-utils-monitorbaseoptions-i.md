# MonitorBaseOptions

监听基础选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface MonitorBaseOptions--><!--Device-unnamed-export declare interface MonitorBaseOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSynchronous

```TypeScript
isSynchronous?: boolean
```

是否同步回调。 true：同步回调；false：异步回调。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorBaseOptions-isSynchronous?: boolean--><!--Device-MonitorBaseOptions-isSynchronous?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## owner

```TypeScript
owner?: IVariableOwner
```

指定冻结的组件，仅能传入@ComponentV2装饰的自定义组件。默认值为 `undefined`，即不指定冻结的组件。

**类型：** [IVariableOwner](arkts-na-decorator-ivariableowner-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorBaseOptions-owner?: IVariableOwner--><!--Device-MonitorBaseOptions-owner?: IVariableOwner-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

