# getVMRuntimeStat

## getVMRuntimeStat

```TypeScript
function getVMRuntimeStat(item: string): number
```

���ݲ�����ȡָ����ϵͳGCͳ����Ϣ��

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | string | 是 | ����ͳ����Ϣ�����͡��ɻ�ȡ��ͳ����Ϣ�������£�"ark.gc.gc-count"����ǰ�̵߳�GC������"ark.gc.gc-time"����ǰ�̴߳�����GC�ܺ�ʱ����msΪ��λ��"ark.gc.gc-bytes-allocated"����ǰ�߳�Ark������ѷ�����ڴ��С����BΪ��λ��"ark.gc.gc-bytes-freed"����ǰ�߳�GC�ɹ����յ��ڴ棬��BΪ��λ��"ark.gc.fullgc-longtime-count"����ǰ�̳߳���fullGC������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ϵͳGCͳ����Ϣ�����ݴ���Ĳ�����������Ӧ����Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Possible causes:1. Invalid parameter, a string parameter required.2. Invalid parameter, unknown property. |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info(`gc-count: ${hidebug.getVMRuntimeStat('ark.gc.gc-count')}`);
  console.info(`gc-time: ${hidebug.getVMRuntimeStat('ark.gc.gc-time')}`);
  console.info(`gc-bytes-allocated: ${hidebug.getVMRuntimeStat('ark.gc.gc-bytes-allocated')}`);
  console.info(`gc-bytes-freed: ${hidebug.getVMRuntimeStat('ark.gc.gc-bytes-freed')}`);
  console.info(`fullgc-longtime-count: ${hidebug.getVMRuntimeStat('ark.gc.fullgc-longtime-count')}`);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

