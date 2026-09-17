# ConnectSettings

连接Wi-Fi设置信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addNetworkToSystem

```TypeScript
addNetworkToSystem?: boolean
```

是否添加网络到系统，true表示将建议网络添加到系统网络中，false表示保持建议网络，默认false 。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## networkId

```TypeScript
networkId: number
```

候选网络配置的ID。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## userActionTimeout

```TypeScript
userActionTimeout?: number
```

提示用户进行信任确认弹框显示时间（单位秒）有效值范围1-30秒，默认10秒 。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## withUserAction

```TypeScript
withUserAction?: boolean
```

连接时是否提示用户进行信任确认，true表示与connectToCandidateConfigWithUserAction接口功能一致，false表示不提示用户进行信任确认，默认false 。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA
