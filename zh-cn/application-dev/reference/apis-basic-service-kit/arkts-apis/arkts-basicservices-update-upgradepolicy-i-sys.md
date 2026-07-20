# UpgradePolicy（系统接口）

升级策略，用于控制升级行为。

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

自动升级时间段，当需要在特定时间段内自动升级时传入此参数(如夜间时段)，此参数为可选参数。不传入此参数时默认为空数组[]，表示不限制自动升级时间段，可在任意时间自动升级。

**类型：** Array&lt;UpgradePeriod&gt;

**起始版本：** 9

<!--Device-UpgradePolicy-autoUpgradePeriods: Array<UpgradePeriod>--><!--Device-UpgradePolicy-autoUpgradePeriods: Array<UpgradePeriod>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## autoUpgradeStrategy

```TypeScript
autoUpgradeStrategy: boolean
```

自动升级策略.true表示可自动升级(适用于希望系统自动完成升级流程的场景，提升用户体验)。false表示不可自动升级(适用于需要用户手动确认升级的场景，避免意外升级或确保用户知情)。根据用户体验需求和升级控制策略选择。

**类型：** boolean

**起始版本：** 9

<!--Device-UpgradePolicy-autoUpgradeStrategy: boolean--><!--Device-UpgradePolicy-autoUpgradeStrategy: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## downloadStrategy

```TypeScript
downloadStrategy: boolean
```

自动下载策略。true表示可自动下载(适用于希望系统自动检测并下载新版本的场景，减少用户手动操作)。false表示不可自动下载(适用于需要用户手动确认下载的场景，避免后台消耗流量或存储空间)。根据用户偏好和流量策略选择。

**类型：** boolean

**起始版本：** 9

<!--Device-UpgradePolicy-downloadStrategy: boolean--><!--Device-UpgradePolicy-downloadStrategy: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

