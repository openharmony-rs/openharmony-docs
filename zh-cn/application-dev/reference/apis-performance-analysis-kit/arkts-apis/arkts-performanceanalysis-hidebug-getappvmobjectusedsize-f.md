# getAppVMObjectUsedSize

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppVMObjectUsedSize

```TypeScript
function getAppVMObjectUsedSize(): bigint
```

获取当前虚拟机中ArkTS对象所占用的内存大小。

**起始版本：** 23

<!--Device-hidebug-function getAppVMObjectUsedSize(): bigint--><!--Device-hidebug-function getAppVMObjectUsedSize(): bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 当前虚拟机中ArkTS对象所占用的内存大小，单位为KB。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

console.info(`getAppVMObjectUsedSize = ${hidebug.getAppVMObjectUsedSize()}`);
```

