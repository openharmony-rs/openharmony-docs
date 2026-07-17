# LeakWatcherConfig

LeakWatcherConfig�������ͣ������а�����������ڴ�й©���Ŀ��������ԡ�

**起始版本：** 24

<!--Device-jsLeakWatcher-interface LeakWatcherConfig--><!--Device-jsLeakWatcher-interface LeakWatcherConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## bgLeakCountThreshold

```TypeScript
bgLeakCountThreshold?: number
```

Ӧ���ں�̨й©�����ﵽ�趨ֵ����dump��ȡֵ��ΧΪ[0, +��)��

GC/Dump�׶Σ����ڵ���1ʱ����Dump��

��ֵĬ��Ϊ1��

���벻��ȡֵ��Χ�ڵ�ֵʱ��ʹ��Ĭ��ֵ��

**类型：** number

**起始版本：** 24

<!--Device-LeakWatcherConfig-bgLeakCountThreshold?: int--><!--Device-LeakWatcherConfig-bgLeakCountThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## checkInterval

```TypeScript
checkInterval?: number
```

ÿ��й©�����ʱ�䣬��λ��ms��ȡֵ��ΧΪ[90000, +��)��

Ĭ��Ϊ90000ms��

���Ӧ��������Զ�������ʱ��С��Ĭ��ֵ��JSLeakWatcherǿ�ƽ��������ΪĬ��ֵ��

��ǰjsLeakWatcherй©������ܿ����ϴ󣬻ᵼ��Ӧ�ÿ��٣���������ò��������ٿ���Ƶ�ʡ�

���벻��ȡֵ��Χ�ڵ�ֵʱ��ʹ��Ĭ��ֵ��

**类型：** number

**起始版本：** 24

<!--Device-LeakWatcherConfig-checkInterval?: int--><!--Device-LeakWatcherConfig-checkInterval?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## dumpHeapWaitTimeMs

```TypeScript
dumpHeapWaitTimeMs?: number
```

�ӳ�ִ��dump����֤GC�ܵ�����ִ������ִ��dump���ӳټ��С�ڵ���й©�����ʱ�䣬��λ��ms��ȡֵ��ΧΪ[0, +��)��

�����ӳ�ʱ������й©���ʱ����Ĭ����й©���ʱ������һ�¡�

��������й©���󽫲��ᴥ��dump��

GC������Ĭ���ӳ�5��ִ��dump��

���벻��ȡֵ��Χ�ڵ�ֵʱ��ʹ��Ĭ��ֵ��

**类型：** number

**起始版本：** 24

<!--Device-LeakWatcherConfig-dumpHeapWaitTimeMs?: int--><!--Device-LeakWatcherConfig-dumpHeapWaitTimeMs?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

���˲�����Ķ���������

������Window��CustomComponent��Ability���������Ӱ������������͵Ĺ��ˡ�

���ڻ�������ʱ�޷����й��ˣ�ֻ�ڿ���̬��Ч��

�������ͻ���ȼ���ID�б� > ��������

Ĭ��Ϊ�����顣

**类型：** Array<string>

**起始版本：** 24

<!--Device-LeakWatcherConfig-exclusionList?: Array<string>--><!--Device-LeakWatcherConfig-exclusionList?: Array<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## fgLeakCountThreshold

```TypeScript
fgLeakCountThreshold?: number
```

Ӧ����ǰ̨й©�����ﵽ�趨ֵ����dump��ȡֵ��ΧΪ[0, +��)��

GC/Dump�׶Σ����ڵ���5ʱ����Dump��

��ֵĬ��Ϊ5��

���벻��ȡֵ��Χ�ڵ�ֵʱ��ʹ��Ĭ��ֵ��

**类型：** number

**起始版本：** 24

<!--Device-LeakWatcherConfig-fgLeakCountThreshold?: int--><!--Device-LeakWatcherConfig-fgLeakCountThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## maxStoredHeapDumps

```TypeScript
maxStoredHeapDumps?: number
```

���dump���������ȡֵ��ΧΪ(0, 10]��������̿ռ�ռ����������ɾ��ʱ�����С��rawheap��jsleaklist�ļ���

Ĭ�ϱ���10��rawheap��10��jsleaklist�ļ���

���벻��ȡֵ��Χ�ڵ�ֵʱ��ʹ��Ĭ��ֵ��

**类型：** number

**起始版本：** 24

<!--Device-LeakWatcherConfig-maxStoredHeapDumps?: int--><!--Device-LeakWatcherConfig-maxStoredHeapDumps?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## monitorObjectTypes

```TypeScript
monitorObjectTypes: MonitorObjectType
```

�����������͡�

Ĭ�ϼ������������͡�

**类型：** MonitorObjectType

**起始版本：** 24

<!--Device-LeakWatcherConfig-monitorObjectTypes: MonitorObjectType--><!--Device-LeakWatcherConfig-monitorObjectTypes: MonitorObjectType-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## objectUniqueIDs

```TypeScript
objectUniqueIDs?: Array<number>
```

�����й©����ID�б���

ֻ�������Զ������������Ӱ������������͵ļ�⡣

���磺�����������õĶ�������ID���Զ���ID�б�������ֵͬʱ����Ч�Զ���ID�б�������

Ĭ��Ϊ�����顣

**类型：** Array<number>

**起始版本：** 24

<!--Device-LeakWatcherConfig-objectUniqueIDs?: Array<int>--><!--Device-LeakWatcherConfig-objectUniqueIDs?: Array<int>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

