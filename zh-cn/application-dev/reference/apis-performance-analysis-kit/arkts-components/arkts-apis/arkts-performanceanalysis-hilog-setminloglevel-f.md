# setMinLogLevel

## 导入模块

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## setMinLogLevel

```TypeScript
function setMinLogLevel(level: LogLevel): void
```

设置应用日志打印的最低日志级别，用于拦截低级别日志打印。

> **注意：**
> 
> 如果设置的日志级别低于[全局日志级别](../../../dfx/hilog.md#查看和设置日志级别)，设置不生效。
> 
> debug版本应用下，此函数不生效。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.HiviewDFX.HiLog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | 是 | 日志级别。 |

**示例**

```TypeScript
以全局日志级别为INFO下，打印5条不同级别的hilog日志，在打印过程中调用两次setMinLogLevel接口为例：
```

```TypeScript
由于全局日志起始为INFO，第一条日志可以正常打印。

在设置进程最低可打印日志级别为WARN后，第二条日志不符合该日志级别，第二条日志打印失败，第三条日志可以正常打印。

在设置进程最低日志级别为DEBUG后，但是此时全局日志级别为INFO，所以第四条日志不满足全局日志级别，打印失败，第五条日志可以打印。

最终打印结果如下所示：
```
