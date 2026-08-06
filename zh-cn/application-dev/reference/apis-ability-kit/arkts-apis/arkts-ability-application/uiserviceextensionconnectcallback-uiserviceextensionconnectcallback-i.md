# UIServiceExtensionConnectCallback

UIServiceExtensionConnectCallback是UIServiceExtension连接回调接口类，提供UIServiceExtension连接回调数据能力。 > **说明：** > > - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export default interface UIServiceExtensionConnectCallback--><!--Device-unnamed-export default interface UIServiceExtensionConnectCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onData

```TypeScript
onData(data: Record<string, Object>): void
```

接收UIServiceExtension连接的回调数据。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-UIServiceExtensionConnectCallback-onData(data: Record<string, Object>): void--><!--Device-UIServiceExtensionConnectCallback-onData(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 接收UIServiceExtension连接回调数据。 |

## onData

```TypeScript
onData(data: Record<string, RecordData>): void
```

Called back when data is sent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceExtensionConnectCallback-onData(data: Record<string, RecordData>): void--><!--Device-UIServiceExtensionConnectCallback-onData(data: Record<string, RecordData>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, \_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 是 | Indicates the received data. |

## onDisconnect

```TypeScript
onDisconnect(): void
```

成功断开UIServiceExtension连接的回调。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-UIServiceExtensionConnectCallback-onDisconnect(): void--><!--Device-UIServiceExtensionConnectCallback-onDisconnect(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

