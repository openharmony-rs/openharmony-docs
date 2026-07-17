# @ohos.fontManager

字体管理模块，提供给系统应用安装和卸载三方字体的能力。

**起始版本：** 19

<!--Device-unnamed-declare namespace fontManager--><!--Device-unnamed-declare namespace fontManager-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [dataMigration](arkts-localization-fontmanager-datamigration-f-sys.md#datamigration-1) | 设备升级时使用的数据迁移接口，用于拉起迁移任务。 |
| [installFont](arkts-localization-fontmanager-installfont-f-sys.md#installfont-1) | 安装指定路径下的字体，使用promise异步回调。 |
| [uninstallFont](arkts-localization-fontmanager-uninstallfont-f-sys.md#uninstallfont-1) | 卸载指定名称的字体，使用promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | 数据迁移时使用的回调类型。 |
| [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | 描述数据迁移的进度信息。 |
<!--DelEnd-->

