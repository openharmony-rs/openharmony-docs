# MatchingWlanInfo

```TypeScript
export interface MatchingWlanInfo
```

匹配的WLAN信息结构体。

**起始版本：** 26.0.0

<!--Device-geoLocationManager-export interface MatchingWlanInfo--><!--Device-geoLocationManager-export interface MatchingWlanInfo-End-->

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## index

```TypeScript
index: number
```

表示匹配的WLAN在wlanBssidArray中的索引。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-MatchingWlanInfo-index: int--><!--Device-MatchingWlanInfo-index: int-End-->

**系统能力：** SystemCapability.Location.Location.Core

## ssid

```TypeScript
ssid: string
```

表示匹配的WLAN的SSID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-MatchingWlanInfo-ssid: string--><!--Device-MatchingWlanInfo-ssid: string-End-->

**系统能力：** SystemCapability.Location.Location.Core
