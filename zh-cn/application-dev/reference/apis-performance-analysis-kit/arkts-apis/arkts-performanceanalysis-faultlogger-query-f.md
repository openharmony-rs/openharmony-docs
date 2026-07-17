# query

## 导入模块

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
```

## query

```TypeScript
function query(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void
```

获取当前应用故障信息，该方法通过回调方式获取故障信息数组，故障信息数组内最多上报10份故障信息。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** addWatcher

<!--Device-FaultLogger-function query(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void--><!--Device-FaultLogger-function query(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| faultType | [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | 是 | 输入要查询的故障类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<FaultLogInfo>> | 是 | 回调函数，在回调函数中获取故障信息数组。<br>value拿到故障信息数组；value为undefined表示获取过程中出现异常，error返回错误提示字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed, Parameter type error |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found |
| [10600001](../errorcode-faultlogger.md#10600001-服务未启动或故障) | The service is not started or is faulty |

**示例：**

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

function queryFaultLogCallback(error: BusinessError, value: Array<FaultLogger.FaultLogInfo>) {
    if (error) {
        console.error(`error code:${error.code}, error msg:${error.message}`);
    } else {
        console.info("value length is " + value.length);
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
try {
    FaultLogger.query(FaultLogger.FaultType.JS_CRASH, queryFaultLogCallback);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}

```


## query

```TypeScript
function query(faultType: FaultType): Promise<Array<FaultLogInfo>>
```

获取当前应用故障信息，该方法通过Promise方式返回故障信息数组，故障信息数组内最多上报10份故障信息。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** addWatcher

<!--Device-FaultLogger-function query(faultType: FaultType): Promise<Array<FaultLogInfo>>--><!--Device-FaultLogger-function query(faultType: FaultType): Promise<Array<FaultLogInfo>>-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| faultType | [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | 是 | 输入要查询的故障类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<FaultLogInfo>> | Promise实例，可以在其then()方法中获取故障信息实例，也可以使用await。<br>value拿到故障信息数组；value为undefined表示获取过程中出现异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed, Parameter type error |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found |
| [10600001](../errorcode-faultlogger.md#10600001-服务未启动或故障) | The service is not started or is faulty |

**示例：**

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getLog() {
  try {
    let value: Array<FaultLogger.FaultLogInfo> = await FaultLogger.query(FaultLogger.FaultType.JS_CRASH);
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
  } catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
  }
}

```

