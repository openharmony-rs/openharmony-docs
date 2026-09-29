# LocationCommand

```TypeScript
export interface LocationCommand
```

扩展命令参数。

**起始版本：** 9

<!--Device-geoLocationManager-export interface LocationCommand--><!--Device-geoLocationManager-export interface LocationCommand-End-->

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## command

```TypeScript
command: string
```

扩展命令字符串，字符串长度不超过100。

**类型：** string

**起始版本：** 9

<!--Device-LocationCommand-command: string--><!--Device-LocationCommand-command: string-End-->

**系统能力：** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario: LocationRequestScenario
```

表示定位场景。

**类型：** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**起始版本：** 9

<!--Device-LocationCommand-scenario: LocationRequestScenario--><!--Device-LocationCommand-scenario: LocationRequestScenario-End-->

**系统能力：** SystemCapability.Location.Location.Core
