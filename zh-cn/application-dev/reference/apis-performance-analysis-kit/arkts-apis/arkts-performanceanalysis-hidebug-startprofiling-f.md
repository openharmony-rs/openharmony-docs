# startProfiling

## startProfiling

```TypeScript
function startProfiling(filename: string): void
```

���������Profiling�������٣�\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_�����ĵ�����Ҫ��\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣��

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [hidebug.startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md#startjscpuprofiling)

<!--Device-hidebug-function startProfiling(filename: string): void--><!--Device-hidebug-function startProfiling(filename: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ���Ĳ������������ļ���������Ӧ�õ�\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Ŀ¼�������Ըò���������json�ļ���string���ȵ����ֵΪ128�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.startProfiling("cpuprofiler-20220216");
// code block
// ...
// code block
hidebug.stopProfiling();
```

