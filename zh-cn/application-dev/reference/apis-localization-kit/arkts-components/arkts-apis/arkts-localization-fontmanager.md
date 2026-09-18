# @ohos.fontManager(字体管理)

本模块为系统应用提供第三方字体的安装、卸载以及字体数据迁移能力。具体为：  
- 安装指定路径的字体文件（支持.ttf、.ttc格式）。  
- 根据字体名称卸载已安装的字体。  
- 在设备升级期间启动字体数据迁移任务，并提供迁移进度和结果回调。

**起始版本：** 19

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
| [dataMigration](arkts-localization-fontmanager-datamigration-f-sys.md) | 设备升级时使用的数据迁移接口，用于启动迁移任务，通过回调函数实时反馈迁移进度和结果。 |
| [installFont](arkts-localization-fontmanager-installfont-f-sys.md) | 将指定路径下的字体文件安装到系统字体库中。使用Promise异步回调。安装成功后，应用可以通过字体名称使用该字体。 |
| [uninstallFont](arkts-localization-fontmanager-uninstallfont-f-sys.md) | 根据字体名称从系统字体库中卸载已安装的字体文件。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | 数据迁移时使用的回调接口类型，定义了数据迁移过程中的回调方法。开发者需实现该接口的所有方法，以接收迁移过程中的心跳通知、进度更新和最终结果。 |
| [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | 描述数据迁移的进度信息，包含进度百分比和预估剩余时间。该接口为数据迁移回调onProgress方法的参数类型。 |
<!--DelEnd-->
