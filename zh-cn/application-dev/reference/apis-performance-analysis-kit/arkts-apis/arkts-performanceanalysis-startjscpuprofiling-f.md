# startJsCpuProfiling

## startJsCpuProfiling

```TypeScript
function startJsCpuProfiling(filename : string) : void
```

���������Profiling�������٣�`startJsCpuProfiling(filename: string)`�����ĵ�����Ҫ��`stopJsCpuProfiling()`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣��

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | �û��Զ���Ĳ������������ļ���������Ӧ�õ�`files`Ŀ¼�������Ըò���������json�ļ���string���ȵ����ֵΪ128�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | the parameter check failed, Parameter type error |

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

