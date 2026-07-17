# startAppTraceCapture

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## startAppTraceCapture

```TypeScript
function startAppTraceCapture(tags: number[], flag: TraceFlag, limitSize: number): string
```

�ýӿڲ�����hitrace���ܣ������߿�ͨ���ýӿ����ָ����Χ��trace�Զ����ɼ������ڸýӿ���trace�ɼ����������ĵ���������Ҫ�ɼ��ķ�Χ������أ����鿪������ʹ�øýӿ�ǰ��ͨ��hitrace����ץȡӦ�õ�trace��־������ɸѡ������trace�ɼ��Ĺؼ���Χ������߸ýӿ����ܡ�`startAppTraceCapture()`�����ĵ�����Ҫ��`stopAppTraceCapture()`�����ĵ���һһ��Ӧ���ظ�����trace�ɼ������½ӿڵ����쳣������trace�ɼ������л����Ľ϶����ܣ�������Ӧ����ɲɼ���ʱ�رա�Ӧ�õ���startAppTraceCapture�ӿ������ɼ�trace�����ɼ���trace��С������limitSize��ϵͳ���Զ�����stopAppTraceCapture�ӿ�ֹͣ�ɼ������limitSize��С���ò���������������trace���ݲ��㣬�޷�������Ϸ���������Ҫ�󿪷��߸���ʵ�����������limitSize��С������������limitSize = Ԥ��trace�ɼ�ʱ�� * trace��λ������Ԥ��trace�ɼ�ʱ���������߸��ݷ����Ĺ��ϳ������о�������λ�롣trace��λ������Ӧ��ÿ�������trace��С��ϵͳ�Ƽ�ֵΪ300KB/s�����鿪���߲�������Ӧ�õ�ʵ��ֵ����λKB/s��trace��λ����ʵ�ⷽ����limitSize����Ϊ���ֵ500M������startAppTraceCapture�ӿڣ���Ӧ���ϲ���N��󣬵���stopAppTraceCaptureֹͣ�ɼ���Ȼ��鿴trace��СS��KB������ôtrace��λ���� = S/N��KB/s����

**起始版本：** 12

<!--Device-hidebug-function startAppTraceCapture(tags: long[], flag: TraceFlag, limitSize: int): string--><!--Device-hidebug-function startAppTraceCapture(tags: long[], flag: TraceFlag, limitSize: int): string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tags | number[] | 是 | trace��Χ���������tags�� |
| flag | [TraceFlag](arkts-performanceanalysis-hidebug-traceflag-e.md) | 是 | �������TraceFlag�� |
| limitSize | number | 是 | ����trace�ļ���С���ƣ���λΪByte��ȡֵ��Χ��0, 500MB]��������Χʱ���ش�����401�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����trace�ļ���·�����ӿڷ�����ʵ����·������Ӧ������Ҫ���ʣ���ο�Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ����·��ת������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid argument, Possible causes:1.The limit parameter is too small2.The parameter is not within the enumeration type3.The parameter type error or parameter order error |
| [11400102](../errorcode-hiviewdfx-hidebug-trace.md#11400102-重复采集) | Capture trace already enabled. |
| [11400103](../errorcode-hiviewdfx-hidebug-trace.md#11400103-权限校验失败) | No write permission on the file. |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Abnormal trace status. |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tags: number[] = [hidebug.tags.ABILITY_MANAGER, hidebug.tags.ARKUI];
let flag: hidebug.TraceFlag = hidebug.TraceFlag.MAIN_THREAD;
let limitSize: number = 1024 * 1024;

try {
  let fileName: string = hidebug.startAppTraceCapture(tags, flag, limitSize);
  console.info(`fileName = ${fileName}`);
  // code block
  // ...
  // code block
  hidebug.stopAppTraceCapture();
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

