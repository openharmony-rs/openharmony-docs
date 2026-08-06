# stopJsCpuProfiling

## stopJsCpuProfiling

```TypeScript
function stopJsCpuProfiling() : void
```

ֹͣ�����Profiling�������٣�\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_�����ĵ�����Ҫ��\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣��

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function stopJsCpuProfiling() : void--><!--Device-hidebug-function stopJsCpuProfiling() : void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.startJsCpuProfiling("cpu_profiling");
  // ...
  hidebug.stopJsCpuProfiling();
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```

