# ConnectSettings

描述WLAN连接的设置信息。

**起始版本：** 26.0.0

<!--Device-wifiManager-interface ConnectSettings--><!--Device-wifiManager-interface ConnectSettings-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## addNetworkToSystem

```TypeScript
addNetworkToSystem?: boolean
```

是否将网络添加到系统中进行连接。 默认为false，如果设置为true，在连接之前会将网络添加到系统中， 且无法再次获取。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectSettings-addNetworkToSystem?: boolean--><!--Device-ConnectSettings-addNetworkToSystem?: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## networkId

```TypeScript
networkId: int
```

WLAN连接的唯一标识ID。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectSettings-networkId: int--><!--Device-ConnectSettings-networkId: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## userActionTimeout

```TypeScript
userActionTimeout?: int
```

用户操作超时阈值（单位为秒）。 最大值不能超过30，默认为10。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectSettings-userActionTimeout?: int--><!--Device-ConnectSettings-userActionTimeout?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## withUserAction

```TypeScript
withUserAction?: boolean
```

随用户操作返回，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ConnectSettings-withUserAction?: boolean--><!--Device-ConnectSettings-withUserAction?: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

