# dumpHeapData

## dumpHeapData

```TypeScript
function dumpHeapData(filename: string): void
```

�����������ת��������\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_�ļ���

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [hidebug.dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md#dumpjsheapdata)(filename

<!--Device-hidebug-function dumpHeapData(filename: string): void--><!--Device-hidebug-function dumpHeapData(filename: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ�����������ת���ļ���������Ӧ�õ�\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Ŀ¼�������Ըò���������heapsnapshot�ļ���string���ȵ����ֵΪ128�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.dumpHeapData("heap-20220216");
```

