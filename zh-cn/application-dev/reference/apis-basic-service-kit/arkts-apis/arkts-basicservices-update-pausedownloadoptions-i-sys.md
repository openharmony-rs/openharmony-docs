# PauseDownloadOptions（系统接口）

暂停下载选项，用于控制暂停行为。对象包含isAllowAutoResume字段，true表示允许自动恢复，false表示需手动恢复。

**起始版本：** 9

<!--Device-update-export interface PauseDownloadOptions--><!--Device-update-export interface PauseDownloadOptions-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## isAllowAutoResume

```TypeScript
isAllowAutoResume: boolean
```

是否允许自动恢复。仅当有正在进行的下载任务时才能设置此参数。

true表示允许自动恢复，系统可能自动恢复下载；false表示不允许，需手动调用resumeDownload恢复。

使用建议：网络不稳定场景建议设置true启用自动恢复，提升下载成功率；需要精确控制下载时机或避免在特定网络环境下恢复的场景建议设置false，通过手动调用resumeDownload控制恢复时机。

**类型：** boolean

**起始版本：** 9

<!--Device-PauseDownloadOptions-isAllowAutoResume: boolean--><!--Device-PauseDownloadOptions-isAllowAutoResume: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

