# stopJsCpuProfiling

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## stopJsCpuProfiling

```TypeScript
function stopJsCpuProfiling() : void
```

ֹͣ�����Profiling�������٣�`stopJsCpuProfiling()`�����ĵ�����Ҫ��`startJsCpuProfiling(filename: string)`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣��

**起始版本：** 9

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

