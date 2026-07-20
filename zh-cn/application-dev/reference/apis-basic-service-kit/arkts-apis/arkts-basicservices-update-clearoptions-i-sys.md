# ClearOptions（系统接口）

清除异常选项，用于指定要清除的异常状态类型。

**起始版本：** 9

<!--Device-update-export interface ClearOptions--><!--Device-update-export interface ClearOptions-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## status

```TypeScript
status: UpgradeStatus
```

异常状态，用于指定要清除的状态。仅当upgrade方法执行失败(状态为UPGRADE_FAIL)后才能设置此参数为UPGRADE_FAIL。

使用场景：当升级失败(状态为UPGRADE_FAIL)后，系统会保留异常状态阻止重新升级，此时需要调用clearError传入status参数清除异常状态，使系统恢复到初始状态以便重新开始升级流程。

常用值：UPGRADE_FAIL(升级失败状态)。注意事项：仅支持清除UPGRADE_FAIL状态。

**类型：** UpgradeStatus

**起始版本：** 9

<!--Device-ClearOptions-status: UpgradeStatus--><!--Device-ClearOptions-status: UpgradeStatus-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

