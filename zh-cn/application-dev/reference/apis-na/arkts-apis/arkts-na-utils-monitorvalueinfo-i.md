# MonitorValueInfo

监听变量信息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface MonitorValueInfo--><!--Device-unnamed-export declare interface MonitorValueInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## observeProps

```TypeScript
observeProps?: boolean
```

是否开启属性观察。 true：开启属性观察；false：不开启属性观察。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorValueInfo-observeProps?: boolean--><!--Device-MonitorValueInfo-observeProps?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path?: string
```

路径信息。未传入将使用自动生成的默认值。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorValueInfo-path?: string--><!--Device-MonitorValueInfo-path?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## valueCallback

```TypeScript
valueCallback: MonitorValueCallback
```

获取变量的回调。

**类型：** [MonitorValueCallback](arkts-na-monitorvaluecallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorValueInfo-valueCallback: MonitorValueCallback--><!--Device-MonitorValueInfo-valueCallback: MonitorValueCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

