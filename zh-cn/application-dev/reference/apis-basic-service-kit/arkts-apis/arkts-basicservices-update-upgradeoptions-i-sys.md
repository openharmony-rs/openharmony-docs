# UpgradeOptions（系统接口）

升级选项，包含升级指令等配置，用于指定升级操作类型。

**起始版本：** 9

<!--Device-update-export interface UpgradeOptions--><!--Device-update-export interface UpgradeOptions-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## order

```TypeScript
order: Order
```

升级指令。用于指定升级操作的执行方式。取值原则：DOWNLOAD仅下载升级包，适用于需要先下载后手动安装的场景；INSTALL仅安装已下载的升级包，适用于已下载完成需直接安装的场景；DOWNLOAD_AND_INSTALL下载并安装，适用于完整升级流程；APPLY仅生效，适用于已安装需重启生效的场景；INSTALL_AND_APPLY安装并生效，适用于安装后立即重启生效的场景。应根据当前升级状态和业务需求选择合适的指令。

**类型：** Order

**起始版本：** 9

<!--Device-UpgradeOptions-order: Order--><!--Device-UpgradeOptions-order: Order-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

