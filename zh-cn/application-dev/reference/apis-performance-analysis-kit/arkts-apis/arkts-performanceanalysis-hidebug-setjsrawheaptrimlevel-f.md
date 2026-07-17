# setJsRawHeapTrimLevel

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

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

<!--Device-hidebug-function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void--><!--Device-hidebug-function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [JsRawHeapTrimLevel](arkts-performanceanalysis-hidebug-jsrawheaptrimlevel-e.md) | 是 | ת���ѿ��յĲü�����Ĭ��ΪTRIM_LEVEL_1�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.setJsRawHeapTrimLevel(hidebug.JsRawHeapTrimLevel.TRIM_LEVEL_2);

```

