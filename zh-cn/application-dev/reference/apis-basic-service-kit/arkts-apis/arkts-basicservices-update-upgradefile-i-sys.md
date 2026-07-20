# UpgradeFile（系统接口）

升级文件，包含文件类型和文件路径，用于指定要安装的本地升级包。

**起始版本：** 9

<!--Device-update-export interface UpgradeFile--><!--Device-update-export interface UpgradeFile-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## filePath

```TypeScript
filePath: string
```

文件路径，支持绝对路径或相对路径。路径长度范围[1，255]，单位：字符，超出范围时抛出异常。

**类型：** string

**起始版本：** 9

<!--Device-UpgradeFile-filePath: string--><!--Device-UpgradeFile-filePath: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## fileType

```TypeScript
fileType: ComponentType
```

文件类型，用于指定升级包类型。设置为OTA表示OTA升级包，系统将根据OTA类型执行固件升级流程，包括完整性校验和系统分区写入等操作。

**类型：** ComponentType

**起始版本：** 9

<!--Device-UpgradeFile-fileType: ComponentType--><!--Device-UpgradeFile-fileType: ComponentType-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

