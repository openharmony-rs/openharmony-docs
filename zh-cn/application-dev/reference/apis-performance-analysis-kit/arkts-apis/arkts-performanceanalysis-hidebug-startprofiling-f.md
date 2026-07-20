# startProfiling

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="startprofiling"></a>
## startProfiling

```TypeScript
function startProfiling(filename: string): void
```

���������Profiling�������٣�`startProfiling(filename: string)`�����ĵ�����Ҫ��`stopProfiling()`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣��

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md#startjscpuprofiling-1)

<!--Device-hidebug-function startProfiling(filename: string): void--><!--Device-hidebug-function startProfiling(filename: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ���Ĳ������������ļ���������Ӧ�õ�`files`Ŀ¼�������Ըò���������json�ļ���string���ȵ����ֵΪ128�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.startProfiling("cpuprofiler-20220216");
// code block
// ...
// code block
hidebug.stopProfiling();

```

