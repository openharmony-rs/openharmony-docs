# TransferMode

表示和远端设备的数据传输模式，为枚举值。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## BASIC

```TypeScript
BASIC = 0
```

表示基础模式，无数据重传机制。适用于对时延和吞吐量敏感的业务场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## RELIABLE

```TypeScript
RELIABLE = 1
```

表示可靠模式，有数据重传机制。适用于对数据完整性要求高的业务场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base
