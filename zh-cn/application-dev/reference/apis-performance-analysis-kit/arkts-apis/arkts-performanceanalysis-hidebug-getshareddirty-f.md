# getSharedDirty

## getSharedDirty

```TypeScript
function getSharedDirty() : bigint
```

��ȡ���̵Ĺ������ڴ��С���ӿ�ʵ�ַ�ʽ����ȡ/proc/{pid}/smaps\_rollup�ڵ��е�Shared\_Dirtyֵ�� > **ע��** > > ����/proc/{pid}/smaps\_rollup�Ķ�ȡ��ʱ�ϳ������鲻Ҫ�����߳���ʹ�øýӿڣ���ͨ��@ohos.taskpool��@ohos.worker�����첽�߳��Ա���Ӧ�ó��ֿ��١�

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getSharedDirty() : bigint--><!--Device-hidebug-function getSharedDirty() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | ���ؽ��̵Ĺ������ڴ��С����λΪKB�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let sharedDirty: bigint = hidebug.getSharedDirty();
console.info(`sharedDirty = ${sharedDirty}`);
```

