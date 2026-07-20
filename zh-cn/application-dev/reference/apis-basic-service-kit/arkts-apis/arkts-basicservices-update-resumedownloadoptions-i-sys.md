# ResumeDownloadOptions（系统接口）

恢复下载选项，用于指定恢复下载的网络类型。对象包含allowNetwork字段，用于设置允许下载的网络类型。

**起始版本：** 9

<!--Device-update-export interface ResumeDownloadOptions--><!--Device-update-export interface ResumeDownloadOptions-End-->

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

网络类型，允许恢复下载的网络类型。仅当已调用pauseDownload暂停下载后才能设置此参数。设置CELLULAR仅允许数据网络恢复下载，设置WIFI仅允许WIFI网络恢复下载，设置CELLULAR_AND_WIFI允许两者均可恢复下载。建议根据升级包大小和网络环境选择：升级包大小超过100MB建议使用WIFI避免流量消耗和提升下载速度；移动场景或无WIFI环境可使用CELLULAR；不确定网络环境建议使用CELLULAR_AND_WIFI。

**类型：** NetType

**起始版本：** 9

<!--Device-ResumeDownloadOptions-allowNetwork: NetType--><!--Device-ResumeDownloadOptions-allowNetwork: NetType-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

