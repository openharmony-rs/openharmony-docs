# setAppResourceLimit

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## setAppResourceLimit

```TypeScript
function setAppResourceLimit(type: string, value: number, enableDebugLog: boolean): void
```

����Ӧ�õ��ļ��������������߳�������JS�ڴ��Native�ڴ���Դ���ơ���ҪӦ�ó������ڹ����ڴ�й©���ϡ�

> **ע��**  
>  
> �������еĿ�����ѡ����ڿ�����ѡ���б����ҵ�"ϵͳ��Դй©��־"�����ã������豸��ӿ���Ч��

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function setAppResourceLimit(type: string, value: int, enableDebugLog: boolean): void--><!--Device-hidebug-function setAppResourceLimit(type: string, value: int, enableDebugLog: boolean): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | й©��Դ���ͣ������֣�  - pss_memory��native�ڴ棩  - js_heap��js���ڴ棩  - fd���ļ���������  - thread���̣߳� |
| value | number | 是 | ��Ӧй©��Դ���͵����ֵ����Χ��  - pss_memory���ͣ�[1024, 4 * 1024 * 1024]����λ��KB��  - js_heap���ͣ�[85, 95]�������JS���ڴ����޵�85%~95%��  - fd���ͣ�[10, 10000]  - thread���ͣ�[1, 1000]��������Χ�ᵼ�¹���ʧЧ�� |
| enableDebugLog | boolean | 是 | �Ƿ������ⲿ������־���ⲿ������־����ڻҶȰ汾����ʽ�汾����֮ǰ������һС�����û��Ƴ��Ĳ��԰汾�������ã���Ϊ�ռ�������־��ռ�ô�����cpu��Դ���ڴ���Դ�����ܻ�����Ӧ�����������⡣true�������ⲿ������־��false�������ⲿ������־�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid argument, Possible causes:1.The limit parameter is too small2.The parameter is not in the specified type3.The parameter type error or parameter order error |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Set limit failed due to remote exception |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let type: string = 'js_heap';
let value: number = 85;
let enableDebugLog: boolean = false;
try {
  hidebug.setAppResourceLimit(type, value, enableDebugLog);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

