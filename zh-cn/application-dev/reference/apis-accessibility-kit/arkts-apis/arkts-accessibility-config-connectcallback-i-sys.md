# ConnectCallback（系统接口）

通过[enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md#enableAbilityWithCallback（系统接口）)接口启用辅助扩展应用时提供的回调函数。辅助扩展应用连接断开时，回调函数将被调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-config-export interface ConnectCallback--><!--Device-config-export interface ConnectCallback-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## onDisconnect

```TypeScript
onDisconnect: OnDisconnectCallback
```

辅助扩展应用的连接断开时调用的回调函数。

**类型：** [OnDisconnectCallback](arkts-accessibility-config-ondisconnectcallback-t-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectCallback-onDisconnect: OnDisconnectCallback--><!--Device-ConnectCallback-onDisconnect: OnDisconnectCallback-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

