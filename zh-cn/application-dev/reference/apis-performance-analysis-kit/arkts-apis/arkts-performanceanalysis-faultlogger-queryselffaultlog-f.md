# querySelfFaultLog

## 导入模块

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
```

## querySelfFaultLog

```TypeScript
function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void
```

获取当前应用故障信息，该方法通过回调方式获取故障信息数组，故障信息数组内最多上报10份故障信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** query

<!--Device-FaultLogger-function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void--><!--Device-FaultLogger-function querySelfFaultLog(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| faultType | [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | 是 | 输入要查询的故障类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<FaultLogInfo>> | 是 | 回调函数，在回调函数中获取故障信息数组。<br>value拿到故障信息数组；value为undefined表示获取过程中出现异常，error返回错误提示字符串。 |

**示例：**

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

function queryFaultLogCallback(error: BusinessError, value: Array<FaultLogger.FaultLogInfo>) {
  if (error) {
    console.error(`error code:${error.code}, error msg:${error.message}`);
  } else {
    console.info(`value length: ${value.length}`);
    let len: number = value.length;
    for (let i = 0; i < len; i++) {
      console.info(`log: ${i}`);
      console.info(`Log pid: ${value[i].pid}`);
      console.info(`Log uid: ${value[i].uid}`);
      console.info(`Log type: ${value[i].type}`);
      console.info(`Log timestamp: ${value[i].timestamp}`);
      console.info(`Log reason: ${value[i].reason}`);
      console.info(`Log module: ${value[i].module}`);
      console.info(`Log summary: ${value[i].summary}`);
      console.info(`Log text: ${value[i].fullLog}`);
    }
  }
}
FaultLogger.querySelfFaultLog(FaultLogger.FaultType.JS_CRASH, queryFaultLogCallback);

```


## querySelfFaultLog

```TypeScript
function querySelfFaultLog(faultType: FaultType): Promise<Array<FaultLogInfo>>
```

获取当前应用故障信息，该方法通过Promise方式返回故障信息数组，故障信息数组内最多上报10份故障信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** query

<!--Device-FaultLogger-function querySelfFaultLog(faultType: FaultType): Promise<Array<FaultLogInfo>>--><!--Device-FaultLogger-function querySelfFaultLog(faultType: FaultType): Promise<Array<FaultLogInfo>>-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| faultType | [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | 是 | 输入要查询的故障类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<FaultLogInfo>> | Promise实例，可以在其then()方法中获取故障信息实例，也可以使用await。<br>value拿到故障信息数组；value为undefined表示获取过程中出现异常。 |

**示例：**

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';

async function getLog() {
  let value: Array<FaultLogger.FaultLogInfo> = await FaultLogger.querySelfFaultLog(FaultLogger.FaultType.JS_CRASH);
  if (value) {
    console.info(`value length: ${value.length}`);
    let len: number = value.length;
    for (let i = 0; i < len; i++) {
      console.info(`log: ${i}`);
      console.info(`Log pid: ${value[i].pid}`);
      console.info(`Log uid: ${value[i].uid}`);
      console.info(`Log type: ${value[i].type}`);
      console.info(`Log timestamp: ${value[i].timestamp}`);
      console.info(`Log reason: ${value[i].reason}`);
      console.info(`Log module: ${value[i].module}`);
      console.info(`Log summary: ${value[i].summary}`);
      console.info(`Log text: ${value[i].fullLog}`);
    }
  }
}

```

