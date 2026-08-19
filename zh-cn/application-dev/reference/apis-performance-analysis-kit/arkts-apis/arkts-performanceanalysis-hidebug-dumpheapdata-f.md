# dumpHeapData

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## dumpHeapData

```TypeScript
function dumpHeapData(filename: string): void
```

虚拟机堆数据转储，生成`filename.heapsnapshot`文件。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md)(filename : string)

<!--Device-hidebug-function dumpHeapData(filename: string): void--><!--Device-hidebug-function dumpHeapData(filename: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 用户自定义的虚拟机堆转储文件名，将在应用的`files`目录下生成以该参数命名的heapsnapshot文件。string长度的最大值为128。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.dumpHeapData("heap-20220216");
```

