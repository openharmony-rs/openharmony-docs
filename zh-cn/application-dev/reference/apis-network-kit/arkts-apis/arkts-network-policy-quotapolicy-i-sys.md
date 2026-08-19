# QuotaPolicy（系统接口）

计量网络策略

**起始版本：** 10

<!--Device-policy-export interface QuotaPolicy--><!--Device-policy-export interface QuotaPolicy-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## lastLimitRemind

```TypeScript
lastLimitRemind?: long
```

最新一次配额耗尽的时间。默认值：-1。

**类型：** long

**起始版本：** 10

<!--Device-QuotaPolicy-lastLimitRemind?: long--><!--Device-QuotaPolicy-lastLimitRemind?: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## lastWarningRemind

```TypeScript
lastWarningRemind?: long
```

最新一次发出警告的时间。默认值：-1。

**类型：** long

**起始版本：** 10

<!--Device-QuotaPolicy-lastWarningRemind?: long--><!--Device-QuotaPolicy-lastWarningRemind?: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## limitAction

```TypeScript
limitAction: LimitAction
```

到达流量限制后的动作。

**类型：** [LimitAction](arkts-network-policy-limitaction-e-sys.md)

**起始版本：** 10

<!--Device-QuotaPolicy-limitAction: LimitAction--><!--Device-QuotaPolicy-limitAction: LimitAction-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## limitBytes

```TypeScript
limitBytes: long
```

流量设置的配额。

**类型：** long

**起始版本：** 10

<!--Device-QuotaPolicy-limitBytes: long--><!--Device-QuotaPolicy-limitBytes: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## metered

```TypeScript
metered: boolean
```

是否为计量网络。true表示是，false表示不是。

**类型：** boolean

**起始版本：** 10

<!--Device-QuotaPolicy-metered: boolean--><!--Device-QuotaPolicy-metered: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## periodDuration

```TypeScript
periodDuration: string
```

流量限制计量周期。D1、M1、Y1分别代表1天、1个月、1年内流量限制，超出时间则不受限制。

**类型：** string

**起始版本：** 10

<!--Device-QuotaPolicy-periodDuration: string--><!--Device-QuotaPolicy-periodDuration: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

## warningBytes

```TypeScript
warningBytes: long
```

发出警告的流量阈值。

**类型：** long

**起始版本：** 10

<!--Device-QuotaPolicy-warningBytes: long--><!--Device-QuotaPolicy-warningBytes: long-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

