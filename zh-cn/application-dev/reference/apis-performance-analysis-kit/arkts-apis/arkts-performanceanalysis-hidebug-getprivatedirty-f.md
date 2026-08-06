# getPrivateDirty

## getPrivateDirty

```TypeScript
function getPrivateDirty() : bigint
```

��ȡ���̵�˽�����ڴ��С����ȡ/proc/{pid}/smaps\_rollup�е�Private\_Dirtyֵ�� > **ע��** > > ����/proc/{pid}/smaps\_rollup�Ķ�ȡ��ʱ�ϳ������鲻Ҫ�����߳���ʹ�øýӿڣ���ͨ��@ohos.taskpool��@ohos.worker�����첽�߳��Ա���Ӧ�ó��ֿ��١�

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getPrivateDirty() : bigint--><!--Device-hidebug-function getPrivateDirty() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | ���ؽ��̵�˽�����ڴ��С����λΪKB�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let privateDirty: bigint = hidebug.getPrivateDirty();
console.info(`privateDirty = ${privateDirty}`);
```

