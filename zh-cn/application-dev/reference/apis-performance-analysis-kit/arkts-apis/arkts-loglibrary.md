# @ohos.logLibrary

本模块提供了获取各类系统维测日志的能力。

**起始版本：** 10

<!--Device-unnamed-declare namespace logLibrary--><!--Device-unnamed-declare namespace logLibrary-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [copy](arkts-performanceanalysis-loglibrary-copy-f-sys.md#copy) | 拷贝指定日志类型的指定文件到目标应用目录下。使用Promise回调。 |
| [copy](arkts-performanceanalysis-loglibrary-copy-f-sys.md#copy-1) | 拷贝指定日志类型的指定文件到目标应用目录下。使用callback回调。 |
| [list](arkts-performanceanalysis-loglibrary-list-f-sys.md#list) | 以同步方法查询指定类型的日志文件列表，接收string类型的对象作为参数，返回指定类型日志的文件列表信息。 |
| [move](arkts-performanceanalysis-loglibrary-move-f-sys.md#move) | 移动指定日志类型的指定文件到目标应用目录下。使用Promise回调。 |
| [move](arkts-performanceanalysis-loglibrary-move-f-sys.md#move-1) | 移动指定日志类型的指定文件到目标应用目录下。使用callback回调。 |
| [remove](arkts-performanceanalysis-loglibrary-remove-f-sys.md#remove) | 以同步方法删除指定日志类型的指定文件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LogEntry](arkts-performanceanalysis-loglibrary-logentry-i-sys.md) | 日志文件对象接口。 |
<!--DelEnd-->

