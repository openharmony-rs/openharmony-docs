# getSystemCpuUsage

## 导入模块

```TypeScript
```

## getSystemCpuUsage

```TypeScript
function getSystemCpuUsage(): number
```

获取系统的CPU资源占用情况。

> **注意**：
> 
> 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 系统CPU资源占用情况。如占用率为50%，则返回0.5。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | The status of the system CPU usage is abnormal. |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info(`getSystemCpuUsage: ${hidebug.getSystemCpuUsage()}`)
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```
