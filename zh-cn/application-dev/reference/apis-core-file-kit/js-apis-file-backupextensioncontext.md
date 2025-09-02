# @ohos.file.BackupExtensionContext (备份恢复扩展能力)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie-->
<!--Designer: @wang_zhangjun; @chenxi0605-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

BackupExtensionContext是BackupExtension的上下文环境，继承自ExtensionContext。

BackupExtensionContext模块提供访问特定BackupExtension的资源的能力。对于拓展的BackupExtension，可直接将BackupExtensionContext作为上下文环境，或者定义一个继承自BackupExtensionContext的类型作为上下文环境。

> **说明：**
>
>  - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>  - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import  { BackupExtensionContext } from '@kit.CoreFileKit';
```

## BackupExtensionContext

### 属性

**系统能力**：SystemCapability.FileManagement.StorageService.Backup

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- |-------| -------- | -------- |
| backupDir<sup>12+</sup> | string | 是 | 否 | 获取备份恢复时的临时路径，该路径只允许在备份恢复过程中作为临时路径使用，不允许应用将该路径作为其他用途来使用。目前只支持el1, el2路径。 |

### 使用场景
BackupExtensionContext主要用于获取备份恢复过程中的临时路径。

**示例：**

```ts
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
import { contextConstant } from '@kit.AbilityKit';

export default class MyBackupExtAbility extends BackupExtensionAbility {
    async onBackup() {
        console.log("onBackup begin");
        // 使用者可通过改变 this.context.area 来进行切换el1，el2对应的沙箱路径
        this.context.area = contextConstant.AreaMode.EL1;
        // 使用者可通过 this.context.backupDir 对沙箱路径进行获取
        let dir = this.context.backupDir;
        console.log(`onBackup el1 dir: ${dir}`);
        this.context.area = contextConstant.AreaMode.EL2;
        dir = this.context.backupDir;
        console.log(`onBackup el2 dir: ${dir}`);
        console.log("onBackup end");
    }

    async onRestore() {
        console.log("onRestore begin");
        this.context.area = contextConstant.AreaMode.EL1;
        let dir = this.context.backupDir;
        console.log(`onRestore el1 dir: ${dir}`);
        this.context.area = contextConstant.AreaMode.EL2;
        dir = this.context.backupDir;
        console.log(`onRestore el2 dir: ${dir}`);
        console.log("onRestore end");
    }
}
```


