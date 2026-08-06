# MonitorOptions

[addMonitor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的可选参数，用于配置回调类型以及是否使能通配符能力。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-unnamed-export interface MonitorOptions--><!--Device-unnamed-export interface MonitorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableWildcard

```TypeScript
enableWildcard?: boolean
```

配置当前addMonitor是否使能通配符能力。true表示使能，false表示关闭。默认值为false，即关闭。当关闭通配符能力，但路径中含有通配符时，该路径将视为不合法路径。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MonitorOptions-enableWildcard?: boolean--><!--Device-MonitorOptions-enableWildcard?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSynchronous

```TypeScript
isSynchronous?: boolean
```

配置当前回调函数是否为同步回调。true为同步回调。默认值为false，即异步回调。

**类型：** boolean

**默认值：** false

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-MonitorOptions-isSynchronous?: boolean--><!--Device-MonitorOptions-isSynchronous?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

