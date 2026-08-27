# startProfiling

## 导入模块

```TypeScript
```

## startProfiling

```TypeScript
function startProfiling(filename: string): void
```


> **说明：**
> 
> 从API version 8支持，从API version 9开始废弃，
> 启动虚拟机Profiling方法跟踪，`startProfiling(filename: string)`方法的调用需要与`stopProfiling()`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，
> 否则会接口调用异常。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md)

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 用户自定义的采样结果输出的文件名，将在应用的`files`目录下生成以该参数命名的json文件。string长度的最大值为128。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.startProfiling("cpuprofiler-20220216");
// code block
// ...
// code block
hidebug.stopProfiling();
```
