# getGraphicsMemory

## getGraphicsMemory

```TypeScript
function getGraphicsMemory(): Promise<int>
```

��ȡӦ���Դ��ܴ�С��gl + graph����ʹ��Promise�첽�ص���

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function getGraphicsMemory(): Promise<int>--><!--Device-hidebug-function getGraphicsMemory(): Promise<int>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | promise���󣬷���Ӧ���Դ��ܴ�С����λΪKB�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Failed to get the application memory due to a remote exception. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { hidebug, hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.getGraphicsMemory().then((ret: number) => {
  console.info(`graphicsMemory: ${ret}`)
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}`);
})
```

ArkTS-Sta示例：

```TypeScript
import { hidebug, hilog } from '@kit.PerformanceAnalysisKit';

hidebug.getGraphicsMemory().then((ret: int) => {
  console.info(`graphicsMemory: ${ret}`)
}).catch((error: Error) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}`);
})
```

