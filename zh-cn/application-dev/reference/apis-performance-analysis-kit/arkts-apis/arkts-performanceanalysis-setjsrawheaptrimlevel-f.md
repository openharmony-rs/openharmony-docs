# setJsRawHeapTrimLevel

## setJsRawHeapTrimLevel

```TypeScript
function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void
```

���õ�ǰ����ת�������ԭʼ�ѿ��յĲü�����ʹ�øýӿڲ��������TRIM_LEVEL_2��������Ч���ٶѿ��յ��ļ���С��

> **ע��**
>
> Ĭ�ϲü�������TRIM_LEVEL_1�����������TRIM_LEVEL_2�ü�����ʹ��API version 20֮���rawheap-translator���߲��ܽ�.rawheap�ļ�ת��Ϊ.heapsnapshot�ļ���������ܵ���ת��ʧ�ܡ�
>
> �ýӿ�Ӱ��dumpJsRawHeapData�Ľ����

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | JsRawHeapTrimLevel | 是 | ת���ѿ��յĲü�����Ĭ��ΪTRIM_LEVEL_1�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.setJsRawHeapTrimLevel(hidebug.JsRawHeapTrimLevel.TRIM_LEVEL_2);

```

