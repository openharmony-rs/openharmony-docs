# isDebugState

## isDebugState

```TypeScript
function isDebugState(): boolean
```

��ȡӦ�ý��̵ĵ���״̬��

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Ӧ�ý��̵�Ark���Native���Ƿ��ڵ���״̬��true�����ڵ���״̬��false��δ���ڵ���״̬�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

console.info(`isDebugState = ${hidebug.isDebugState()}`)

```

