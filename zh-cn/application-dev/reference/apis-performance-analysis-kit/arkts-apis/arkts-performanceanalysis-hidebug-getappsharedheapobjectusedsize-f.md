# getAppSharedHeapObjectUsedSize

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppSharedHeapObjectUsedSize

```TypeScript
function getAppSharedHeapObjectUsedSize(): bigint
```

获取虚拟机中共享堆对象所占用的内存大小。

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-hidebug-function getAppSharedHeapObjectUsedSize(): bigint--><!--Device-hidebug-function getAppSharedHeapObjectUsedSize(): bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 虚拟机中共享堆对象所占用的内存大小, 单位为KB。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | VM instance exception. |
