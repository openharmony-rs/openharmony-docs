# DownloadOptions（系统接口）

下载选项，包含allowNetwork(允许下载的网络类型)和order(升级指令)字段，用于控制下载行为。

**起始版本：** 9

<!--Device-update-export interface DownloadOptions--><!--Device-update-export interface DownloadOptions-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## allowNetwork

```TypeScript
allowNetwork: NetType
```

网络类型，允许下载的网络类型。设置CELLULAR仅允许数据网络下载，设置WIFI仅允许WIFI下载，设置CELLULAR_AND_WIFI允许两者均可下载。建议根据升级包大小和网络环境选择：大文件升级包建议使用WIFI避免流量消耗和提升下载速度；移动场景或无WIFI环境可使用CELLULAR；不确定网络环境建议使用CELLULAR_AND_WIFI。

**类型：** NetType

**起始版本：** 9

<!--Device-DownloadOptions-allowNetwork: NetType--><!--Device-DownloadOptions-allowNetwork: NetType-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## order

```TypeScript
order: Order
```

取值原则：DOWNLOAD仅下载，适用于先下载后手动安装场景；INSTALL仅安装，适用于直接安装已下载的升级包场景；DOWNLOAD_AND_INSTALL下载并安装，适用于完整升级流程；APPLY仅生效，适用于已安装需重启生效场景；INSTALL_AND_APPLY安装并生效，适用于安装后立即重启生效场景。

**类型：** Order

**起始版本：** 9

<!--Device-DownloadOptions-order: Order--><!--Device-DownloadOptions-order: Order-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

