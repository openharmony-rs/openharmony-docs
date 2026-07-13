# dumpHeapData

## dumpHeapData

```TypeScript
function dumpHeapData(filename: string): void
```

�����������ת��������`filename.heapsnapshot`�ļ���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** dumpJsHeapData(filename

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ�����������ת���ļ���������Ӧ�õ�`files`Ŀ¼�������Ըò���������heapsnapshot�ļ���string���ȵ����ֵΪ128�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.dumpHeapData("heap-20220216");

```

