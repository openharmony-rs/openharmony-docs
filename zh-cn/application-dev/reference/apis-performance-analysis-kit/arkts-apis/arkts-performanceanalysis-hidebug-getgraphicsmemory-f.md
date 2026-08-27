# getGraphicsMemory

## 导入模块

```TypeScript
```

## getGraphicsMemory

```TypeScript
function getGraphicsMemory(): Promise<number>
```

获取应用显存总大小（gl + graph），使用Promise异步回调。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | promise对象，返回应用显存总大小，单位为KB。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Failed to get the application memory due to a remote exception. |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.getGraphicsMemory().then((ret: number) => {
  console.info(`graphicsMemory: ${ret}`)
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}`);
})
```
