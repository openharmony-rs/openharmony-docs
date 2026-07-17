# getPss

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getPss

```TypeScript
function getPss() : bigint
```

��ȡӦ�ý���ʵ��ʹ�õ������ڴ��С���ӿ�ʵ�ַ�ʽ����ȡ/proc/{pid}/smaps_rollup�ڵ��е�Pss��SwapPssֵ����͡�

> **ע��**  
>  
> ����/proc/{pid}/smaps_rollup�Ķ�ȡ��ʱ�ϳ������鲻Ҫ�����߳���ʹ�øýӿڣ���ͨ��@ohos.taskpool��@ohos.worker�����첽�߳��Ա���Ӧ�ó��ֿ��١�

**起始版本：** 8

<!--Device-hidebug-function getPss() : bigint--><!--Device-hidebug-function getPss() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | ����Ӧ�ý���ʵ��ʹ�õ������ڴ��С����λΪKB�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let pss: bigint = hidebug.getPss();
console.info(`pss = ${pss}`);

```

