# setJsRawHeapTrimLevel

## setJsRawHeapTrimLevel

```TypeScript
function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void
```

���õ�ǰ����ת�������ԭʼ�ѿ��յĲü�����ʹ�øýӿڲ��������TRIM\_LEVEL\_2��������Ч���ٶѿ��յ��ļ���С�� > **ע��** > > Ĭ�ϲü�������TRIM\_LEVEL\_1�����������TRIM\_LEVEL\_2�ü�����ʹ��API version 20֮���rawheap-translator���߲��ܽ�.rawheap�ļ�ת��Ϊ.heapsnapshot�ļ���������ܵ���ת��ʧ�ܡ� > > �ýӿ�Ӱ��dumpJsRawHeapData�Ľ����

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为26.1.0。

<!--Device-hidebug-function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void--><!--Device-hidebug-function setJsRawHeapTrimLevel(level: JsRawHeapTrimLevel): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ת���ѿ��յĲü�����Ĭ��ΪTRIM\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEVEL\_\_\_ESCAPED\_UNDERSCORE\_\_\_1�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.setJsRawHeapTrimLevel(hidebug.JsRawHeapTrimLevel.TRIM_LEVEL_2);
```

