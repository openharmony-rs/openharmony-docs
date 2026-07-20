# setProcDumpInSharedOOM

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="setprocdumpinsharedoom"></a>
## setProcDumpInSharedOOM

```TypeScript
function setProcDumpInSharedOOM(enable: boolean): void
```

��ת���Ķѿ������̼߳���Ϊ���̼���

> **ע��**  
>  
> Ҫ��ת�����̼��Ķѿ��գ����øýӿڲ�����true������OOMʱ��������SharedHeap OOM����������ȱһ���ɡ�  
>  
> �ýӿڲ�Ӱ������������ת���Ķѿ������ݡ��磺����Ӱ��dumpJsRawHeapData�Ľ����  
>  
> �ýӿ���Ӧ�õ����������ڿɱ���ε��ã��������һ�ε��õ�ִ�н������Ч��

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function setProcDumpInSharedOOM(enable: boolean): void--><!--Device-hidebug-function setProcDumpInSharedOOM(enable: boolean): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | �����̷���SharedHeap OOMʱ��ϵͳ�����ݸý��������������������һ�ε��øýӿ�����¼����Ϣ��ת����Ӧ����Ķѿ��ա�true�����̼���false���̼߳���Ĭ��ֵ��false�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.setProcDumpInSharedOOM(true);

```

