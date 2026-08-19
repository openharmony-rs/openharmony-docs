# IMonitorPathInfo

Defines Monitor path with its accessor interface.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IMonitorPathInfo--><!--Device-unnamed-export declare interface IMonitorPathInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableWildcard

```TypeScript
enableWildcard?: boolean
```

启用通配符功能。 设置为true可启用通配符功能，设置为false可禁用通配符功能。 默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitorPathInfo-enableWildcard?: boolean--><!--Device-IMonitorPathInfo-enableWildcard?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

Changed paths(keys)

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitorPathInfo-path: string--><!--Device-IMonitorPathInfo-path: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## valueCallback

```TypeScript
valueCallback: MonitorValueCallback
```

Callback function to access monitored value.

**类型：** [MonitorValueCallback](arkts-na-monitorvaluecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitorPathInfo-valueCallback: MonitorValueCallback--><!--Device-IMonitorPathInfo-valueCallback: MonitorValueCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

