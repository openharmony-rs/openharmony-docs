# getCpuUsage

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getCpuUsage

```TypeScript
function getCpuUsage() : number
```

获取进程的CPU使用率。

> **注意**：
> 
> 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取进程的CPU使用率。如占用率为50%，则返回0.5。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let cpuUsage: number = hidebug.getCpuUsage();
console.info(`cpuUsage = ${cpuUsage}`);
```
