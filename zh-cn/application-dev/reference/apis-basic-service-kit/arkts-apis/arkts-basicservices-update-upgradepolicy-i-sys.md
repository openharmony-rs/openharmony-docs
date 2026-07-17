# UpgradePolicy（系统接口）

升级策略。

**起始版本：** 9

<!--Device-update-export interface UpgradePolicy--><!--Device-update-export interface UpgradePolicy-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## autoUpgradePeriods

```TypeScript
autoUpgradePeriods: Array<UpgradePeriod>
```

自动升级时间段。

**类型：** Array<UpgradePeriod>

**起始版本：** 9

<!--Device-UpgradePolicy-autoUpgradePeriods: Array<UpgradePeriod>--><!--Device-UpgradePolicy-autoUpgradePeriods: Array<UpgradePeriod>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## autoUpgradeStrategy

```TypeScript
autoUpgradeStrategy: boolean
```

自动升级策略。

true表示可自动升级，false表示不可自动升级。

**类型：** boolean

**起始版本：** 9

<!--Device-UpgradePolicy-autoUpgradeStrategy: boolean--><!--Device-UpgradePolicy-autoUpgradeStrategy: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## downloadStrategy

```TypeScript
downloadStrategy: boolean
```

自动下载策略。

true表示可自动下载，false表示不可自动下载。

**类型：** boolean

**起始版本：** 9

<!--Device-UpgradePolicy-downloadStrategy: boolean--><!--Device-UpgradePolicy-downloadStrategy: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

