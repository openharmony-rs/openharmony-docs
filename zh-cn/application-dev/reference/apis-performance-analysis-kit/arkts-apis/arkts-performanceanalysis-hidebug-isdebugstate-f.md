# isDebugState

## isDebugState

```TypeScript
function isDebugState(): boolean
```

��ȡӦ�ý��̵ĵ���״̬��

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function isDebugState(): boolean--><!--Device-hidebug-function isDebugState(): boolean-End-->

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

