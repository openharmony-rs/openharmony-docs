# getAppVMObjectUsedSize

## getAppVMObjectUsedSize

```TypeScript
function getAppVMObjectUsedSize(): bigint
```

��ȡ��ǰ�������ArkTS������ռ�õ��ڴ��С��

**起始版本：** 21

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | ��ǰ�������ArkTS������ռ�õ��ڴ��С����λΪKB�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

console.info(`getAppVMObjectUsedSize = ${hidebug.getAppVMObjectUsedSize()}`);

```

