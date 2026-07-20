# UpgradePeriod（系统接口）

升级时间段。

**起始版本：** 9

<!--Device-update-export interface UpgradePeriod--><!--Device-update-export interface UpgradePeriod-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## end

```TypeScript
end: number
```

结束时间，取值范围[0, 1440]，单位为min。表示一天中的分钟数，0表示00:00，1440表示24:00。

必须大于或等于start，超出范围时抛出异常。

**类型：** number

**起始版本：** 9

<!--Device-UpgradePeriod-end: int--><!--Device-UpgradePeriod-end: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## start

```TypeScript
start: number
```

开始时间，取值范围[0, 1440]，单位为min。表示一天中的分钟数，0表示00:00，1440表示24:00。

必须小于或等于end，超出范围时抛出异常。

**类型：** number

**起始版本：** 9

<!--Device-UpgradePeriod-start: int--><!--Device-UpgradePeriod-start: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

