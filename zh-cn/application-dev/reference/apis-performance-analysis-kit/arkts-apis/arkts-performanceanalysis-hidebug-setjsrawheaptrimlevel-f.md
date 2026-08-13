# setJsRawHeapTrimLevel

## setJsRawHeapTrimLevel

```TypeScript
function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void
```

设置当前进程转储虚拟机原始堆快照的裁剪级别。使用该接口并传入参数TRIM_LEVEL_2，可以有效减少堆快照的文件大小。 > **注意** > > 默认裁剪级别是TRIM_LEVEL_1。如果设置了TRIM_LEVEL_2裁剪，需使用API version 20之后的rawheap-translator工具才能将.rawheap文件转换为.heapsnapshot文件，否则可能导致转换失败。 > > 该接口影响dumpJsRawHeapData的结果。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

<!--Device-hidebug-function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void--><!--Device-hidebug-function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [JsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-jsrawheaptrimlevel-e.md) | 是 | 转储堆快照的裁剪级别，默认为TRIM_LEVEL_1。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.setJsRawHeapTrimLevel(hidebug.JsRawHeapTrimLevel.TRIM_LEVEL_2);
```

