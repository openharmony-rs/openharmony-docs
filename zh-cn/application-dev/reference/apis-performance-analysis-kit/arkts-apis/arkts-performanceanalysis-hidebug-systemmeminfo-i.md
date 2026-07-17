# SystemMemInfo

����ϵͳ�ڴ���Ϣ���������ڴ桢�����ڴ�Ϳ����ڴ档

**起始版本：** 12

<!--Device-hidebug-interface SystemMemInfo--><!--Device-hidebug-interface SystemMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## availableMem

```TypeScript
availableMem: bigint
```

ϵͳ���õ��ڴ棬��KBΪ��λ�����㷽ʽ��/proc/meminfo: MemAvailable��

**类型：** bigint

**起始版本：** 12

<!--Device-SystemMemInfo-availableMem: bigint--><!--Device-SystemMemInfo-availableMem: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## freeMem

```TypeScript
freeMem: bigint
```

ϵͳ���е��ڴ棬��KBΪ��λ�����㷽ʽ��/proc/meminfo: MemFree��

**类型：** bigint

**起始版本：** 12

<!--Device-SystemMemInfo-freeMem: bigint--><!--Device-SystemMemInfo-freeMem: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## totalMem

```TypeScript
totalMem: bigint
```

ϵͳ�ܵ��ڴ棬��KBΪ��λ�����㷽ʽ��/proc/meminfo: MemTotal��

**类型：** bigint

**起始版本：** 12

<!--Device-SystemMemInfo-totalMem: bigint--><!--Device-SystemMemInfo-totalMem: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

