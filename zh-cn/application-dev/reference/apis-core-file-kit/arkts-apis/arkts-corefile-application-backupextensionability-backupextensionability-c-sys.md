# BackupExtensionAbility

备份恢复扩展能力。应用可通过该类实现自定义备份、恢复、进度上报和安全退出逻辑。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

## 导入模块

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
```

## getBackupCompatibilityInfo

```TypeScript
getBackupCompatibilityInfo(extInfo: string) : Promise<string>
```

在应用备份阶段，调用方获取应用自定义兼容性信息时执行，由应用实现返回。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extInfo | string | 是 | 传递给应用的额外信息，由应用自行处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回备份过程中应用自定义的兼容性信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class BackupExt extends BackupExtensionAbility {
  async getBackupCompatibilityInfo(extInfo: string): Promise<string> {
    let ret: string = '';
    try {
      // 此处仅以JSON为示范，相应判断逻辑及相应字段由应用自定义
      if (!extInfo) {
        ret = '{"dbVersion": "1.0", "isThemCardEnable": "true"}';
      } else {
        let extJson: Record<string, string> = JSON.parse(extInfo);
        if (extJson?.requireCompatibility) {
          ret = '{"isSupportBackup": "true"}';
        } else {
          ret = '{"isSupportBackup": "false"}';
        }
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getBackupCompatibilityInfo failed with error. Code: ${err.code}, message: ${err.message}`);
    }
    return ret;
  }
}
```

## getBackupInfo

```TypeScript
getBackupInfo(): string
```

在调用方查询应用数据时执行，由应用返回自定义备份信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用自定义的备份信息，具体格式和字段由应用自行定义。 |

**示例**

```TypeScript
class BackupExt extends BackupExtensionAbility {
  getBackupInfo(): string {
    console.info('getBackupInfo ok');
    let info = 'app diy info';
    return info;
  }
}
```

## getRestoreCompatibilityInfo

```TypeScript
getRestoreCompatibilityInfo(extInfo: string) : Promise<string>
```

在应用恢复阶段，调用方获取应用自定义兼容性信息时执行，由应用实现返回。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extInfo | string | 是 | 传递给应用的额外信息，由应用自行处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象，返回恢复过程中应用自定义的兼容性信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class BackupExt extends BackupExtensionAbility {
  async getRestoreCompatibilityInfo(extInfo: string): Promise<string> {
    let ret: string = '';
    try {
      // 此处仅以JSON为示范，相应判断逻辑及相应字段由应用自定义
      if (!extInfo) {
        ret = '{"dbVersion": "1.0", "isThemCardEnable": "true"}';
      } else {
        let extJson: Record<string, string> = JSON.parse(extInfo);
        if (extJson?.requireCompatibility) {
          ret = '{"isSupportRestore": "true"}';
        } else {
          ret = '{"isSupportRestore": "false"}';
        }
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`getRestoreCompatibilityInfo failed with error. Code: ${err.code}, message: ${err.message}`);
    }
    return ret;
  }
}
```
