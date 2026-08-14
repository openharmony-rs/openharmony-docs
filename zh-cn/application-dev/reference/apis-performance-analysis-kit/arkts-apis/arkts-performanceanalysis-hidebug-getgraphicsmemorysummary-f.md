# getGraphicsMemorySummary

## getGraphicsMemorySummary

```TypeScript
function getGraphicsMemorySummary(interval?: int): Promise<GraphicsMemorySummary>
```

获取应用显存数据，使用Promise进行异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function getGraphicsMemorySummary(interval?: int): Promise<GraphicsMemorySummary>--><!--Device-hidebug-function getGraphicsMemorySummary(interval?: int): Promise<GraphicsMemorySummary>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interval | int | 否 | 显存数据缓存值有效时间，单位为秒。默认值：300。取值范围为[2-3600]。若传入值超出取值范围时，将使用默认值。 当显存数据缓存值存在时间超过该值时，获取最新显存数据并更新缓存值；否则，直接获取缓存值。 取值范围为全体整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[GraphicsMemorySummary](arkts-performanceanalysis-hidebug-graphicsmemorysummary-i.md)&gt; | promise对象，返回应用显存数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Failed to get the application memory due to a remote exception. |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.getGraphicsMemorySummary().then((ret: hidebug.GraphicsMemorySummary) => {
  console.info(`get graphicsMemory gl: ${ret.gl} graph: ${ret.graph}.`)
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}.`);
})
```

