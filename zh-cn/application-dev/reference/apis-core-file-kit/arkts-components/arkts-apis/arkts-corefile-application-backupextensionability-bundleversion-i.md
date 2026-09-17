# BundleVersion

恢复时所需要的版本信息，开发者可根据配置的版本号来判断本次恢复时的应用版本数据。

@interface BundleVersion

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

## 导入模块

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
```

## code

```TypeScript
code: number
```

应用的版本号。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

## name

```TypeScript
name: string
```

应用的版本名称。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.Backup
