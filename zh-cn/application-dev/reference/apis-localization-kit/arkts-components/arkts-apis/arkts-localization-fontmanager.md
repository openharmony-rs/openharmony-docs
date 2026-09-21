# @ohos.fontManager(字体管理)

本模块为应用提供第三方字体的安装、卸载、查询以及字体服状态监听能力。具体为：<br>- 安装应用级或会话级字体文件，支持`.ttf`、`.ttc`、`.otf` 格式。<br>- 根据字体路径卸载已安装的字体。<br>- 查询已安装字体的作用范围。<br>- 注册字体服务状态变化监听器，当字体服务异常退出时通知应用。

**起始版本：** 19

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getFontScope](arkts-localization-fontmanager-getfontscope-f.md) | 查询指定路径字体的作用范围。使用Promise异步回调。 |
| [installScopeFont](arkts-localization-fontmanager-installscopefont-f.md) | 安装指定路径下的字体文件为应用级或会话级字体。使用Promise异步回调。 |
| [offFontObserver](arkts-localization-fontmanager-offfontobserver-f.md) | 注销字体服务状态变化监听器。 |
| [onFontObserver](arkts-localization-fontmanager-onfontobserver-f.md) | 注册字体服务状态变化监听器。 |
| [uninstallScopeFont](arkts-localization-fontmanager-uninstallscopefont-f.md) | 根据字体路径卸载已安装的应用级或会话级字体。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [dataMigration](arkts-localization-fontmanager-datamigration-f-sys.md) | 设备升级时使用的数据迁移接口，用于启动迁移任务，通过回调函数实时反馈迁移进度和结果。 |
| [installFont](arkts-localization-fontmanager-installfont-f-sys.md) | 将指定路径下的字体文件安装到系统字体库中。使用Promise异步回调。 |
| [uninstallFont](arkts-localization-fontmanager-uninstallfont-f-sys.md) | 根据字体名称从系统字体库中卸载已安装的字体文件。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [FontClientObserver](arkts-localization-fontmanager-fontclientobserver-i.md) | 字体服务状态变化监听器。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | 数据迁移时使用的回调接口类型，定义了数据迁移过程中的回调方法。开发者需实现该接口的所有方法，以接收迁移过程中的心跳通知、进度更新和最终结果。 |
| [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | 描述数据迁移的进度信息，包含进度百分比和预估剩余时间。该接口为数据迁移回调onProgress方法的参数类型。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FontScope](arkts-localization-fontmanager-fontscope-e.md) | 表示字体作用范围的枚举。 |
