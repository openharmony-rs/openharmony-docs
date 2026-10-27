# LocationAttributes（系统接口）

```TypeScript
export interface LocationAttributes
```

位置类场景属性。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface LocationAttributes--><!--Device-behaviorAwareness-export interface LocationAttributes-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## coordinates

```TypeScript
coordinates: Coordinates
```

地理坐标。

**类型：** [Coordinates](arkts-multimodalawareness-behaviorawareness-coordinates-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationAttributes-coordinates: Coordinates--><!--Device-LocationAttributes-coordinates: Coordinates-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## kind

```TypeScript
kind: 'location'
```

判别字段，固定为 'location'。

**类型：** 'location'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationAttributes-kind: 'location'--><!--Device-LocationAttributes-kind: 'location'-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## locationName

```TypeScript
locationName?: string
```

位置名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationAttributes-locationName?: string--><!--Device-LocationAttributes-locationName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## locationType

```TypeScript
locationType?: LocationType
```

位置类型。

**类型：** [LocationType](arkts-multimodalawareness-behaviorawareness-locationtype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocationAttributes-locationType?: LocationType--><!--Device-LocationAttributes-locationType?: LocationType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
