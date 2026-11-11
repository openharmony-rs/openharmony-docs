# @ohos.hiSysEvent (System Event Logging) (System API)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @buzhenwang-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=d0df7443e82c4838dce785dd4842b0395a795402 translatedAt=2026-11-03T06:20:53.524Z pushedAt=2026-11-03T12:08:25.618Z nl=1 -->

This module provides the event logging capability, including event tracking of system events, subscription to persisted system events, and query of persisted system events. It is applicable to scenarios such as system fault diagnosis, performance monitoring, and user behavior analysis, helping developers quickly locate and resolve issues and improving system observability and O&M efficiency.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## EventType

Enumerates event types.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Value| Description|
| -------- | -------- | -------- |
| FAULT | 1 | Error event.|
| STATISTIC | 2 | Statistic event.|
| SECURITY | 3 | Security event.|
| BEHAVIOR | 4 | User behavior event.|

## SysEventInfo

Defines a system event.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| domain | string | No| No| Event domain.|
| name | string | No| No| Event name.|
| eventType | [EventType](#eventtype) | No| No| Event type.|
| params | object | No | Yes | Event parameters. The parameters must meet the requirements such as validation, string type parameter size limit, total parameter count limit, and array type parameter count limit. For details, see [System Event Error Codes](errorcode-hisysevent-sys.md): 11200001-11200054. |


## hiSysEvent.write

write(info: SysEventInfo, callback: AsyncCallback&lt;void&gt;): void

Event logging API. It receives an object of the [SysEventInfo](#syseventinfo) type as the event parameter and uses an asynchronous callback. Applicable to scenarios where system events need to be logged asynchronously to avoid blocking the main thread, which can improve application response performance.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name   | Type                     | Mandatory| Description                                                        |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| info | [SysEventInfo](#syseventinfo) | Yes | System Event information object, which contains the Event Domain, Event Name, Event Type, and Event Parameters. |
| callback  | AsyncCallback&lt;void&gt; | Yes | Callback Function used to handle the return value of the API.<br>- 0 indicates that the event verification succeeds and the event is written to the event file asynchronously;<br>- A positive value indicates that an exception occurs during Event Logging, but the event can still be written normally;<br>- A negative value indicates that Event Logging fails. |

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200001 | Invalid event domain.                                                                                                                           |
| 11200002 | Invalid event name.                                                                                                                             |
| 11200003 | Abnormal environment.                                                                                                                           |
| 11200004 | The event length exceeds the limit.                                                                                                             |
| 11200051 | Invalid event parameter.                                                                                                                        |
| 11200052 | The size of the event parameter of the string type exceeds the limit.                                                                           |
| 11200053 | The number of event parameters exceeds the limit.                                                                                               |
| 11200054 | The number of event parameters of the array type exceeds the limit.                                                                             |

**Example**

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo, (err: BusinessError) => {
    // Handle the operations after the event is written successfully.
  });
} catch (err) {
  // Catch and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```


## hiSysEvent.write

write(info: SysEventInfo): Promise&lt;void&gt;

Event logging API. It receives an object of the [SysEventInfo](#syseventinfo) type as the event parameter and uses a Promise for asynchronous callback. Applicable to scenarios where chained calls are needed to handle asynchronous results, which can make the code more concise and elegant.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name   | Type                   | Mandatory| Description|
| --------- | ----------------------- | ---- | --------------- |
| info | [SysEventInfo](#syseventinfo) | Yes  | System event information.|

**Return value**

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise instance, which can be used to handle the callbacks for successful and abnormal System Event writing in its then() and catch() callback methods, respectively. |

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200001 | Invalid event domain.                                                                                                                           |
| 11200002 | Invalid event name.                                                                                                                             |
| 11200003 | Abnormal environment.                                                                                                                           |
| 11200004 | The event length exceeds the limit.                                                                                                             |
| 11200051 | Invalid event parameter.                                                                                                                        |
| 11200052 | The size of the event parameter of the string type exceeds the limit.                                                                           |
| 11200053 | The number of event parameters exceeds the limit.                                                                                               |
| 11200054 | The number of event parameters of the array type exceeds the limit.                                                                             |

**Example**

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  // Write a system event in Promise mode, handle the success event in then, and handle the error in catch.
  hiSysEvent.write(eventInfo).then(
    () => {
      // Handle the operation after the event is written successfully.
    }
  ).catch(
    (err: BusinessError) => {
      // Catch and print the error message.
      console.error(`error code: ${err.code}, error msg: ${err.message}`);
    }
  );
} catch (err) {
  // Catch and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

## RuleType

Enumerates matching rule types.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Value| Description|
| -------- | -------- | -------- |
| WHOLE_WORD | 1 | Whole word matching.|
| PREFIX | 2 | Prefix matching.|
| REGULAR | 3 | Regular expression matching.|

## WatchRule

Defines event subscription rules.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| domain | string | No| No| Event domain.|
| name | string | No| No| Event name.|
| tag | string | No | Yes | Event tag. If omitted, an empty string is used as the default value. |
| ruleType | [RuleType](#ruletype) | No| No| Matching rule type.|

## Watcher

Defines a watcher for event subscription.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| rules | [WatchRule](#watchrule)[] | No| No| Array of matching event subscription rules.|
| onEvent | function | No | No | Callback invoked when a subscribed event occurs. The callback receives the subscribed [SysEventInfo](#syseventinfo) and is used to handle the subscribed event data. |
| onServiceDied | function | No | No | Callback invoked when the system event service is closed. It is triggered when the system event service is closed or stopped abnormally, and is used to handle service exceptions (such as recording logs and resubscribing to events). |

## hiSysEvent.addWatcher

addWatcher(watcher: Watcher): void

Subscribes to system events and receives an object of the [Watcher](#watcher) type as the event parameter. Applicable to scenarios where system events need to be monitored in real time.

**Required permission**: ohos.permission.READ_DFX_SYSEVENT

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ----------------------------- | ---- | ------------------------ |
| watcher | [Watcher](#watcher) | Yes| Watcher for event subscription.|

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT.                         |
| 202      | System API is not allowed called by Non-system application.                                                                                     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200101 | The number of watchers exceeds the limit.                                                                                                       |
| 11200102 | The number of watch rules exceeds the limit.                                                                                                    |

**Example**

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let watchRules: hiSysEvent.WatchRule[] = [{
    domain: "RELIABILITY",
    name: "STACK",
    tag: "STABILITY",
    ruleType: hiSysEvent.RuleType.WHOLE_WORD,
  } as hiSysEvent.WatchRule];
let watcher: hiSysEvent.Watcher = {
  rules: watchRules,
  onEvent: (info: hiSysEvent.SysEventInfo) => {
    // Handle the subscribed system event.
  },
  onServiceDied: () => {
    // Handle the system event service exception.
  }
};
try {
  hiSysEvent.addWatcher(watcher);
} catch (err) {
  // Capture and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

## hiSysEvent.removeWatcher

removeWatcher(watcher: Watcher): void

Unsubscribes from system events and receives an object of the [Watcher](#watcher) type as the event parameter. Applicable to scenarios where monitoring of certain events is no longer needed. After the unsubscription succeeds, the subscriber will no longer receive events.

**Required permission**: ohos.permission.READ_DFX_SYSEVENT

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name| Type | Mandatory| Description |
| ------ | ------------- | ---- | ------------------------- |
| watcher | [Watcher](#watcher) | Yes| Watcher for event subscription.|

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT.                         |
| 202      | System API is not allowed called by Non-system application.                                                                                     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200201 | The watcher does not exist.                                                                                                                     |

**Example**

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let watchRules: hiSysEvent.WatchRule[] = [{
    domain: "RELIABILITY",
    name: "STACK",
    tag: "STABILITY",
    ruleType: hiSysEvent.RuleType.WHOLE_WORD,
  } as hiSysEvent.WatchRule ];
let watcher: hiSysEvent.Watcher = {
  rules: watchRules,
  onEvent: (info: hiSysEvent.SysEventInfo) => {
    // Handle the subscribed system event.
  },
  onServiceDied: () => {
    // Handle the system event service exception.
  }
};
try {
  hiSysEvent.addWatcher(watcher);
  hiSysEvent.removeWatcher(watcher);
} catch (err) {
  // Capture and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

## QueryArg

Defines arguments for an event query.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| beginTime | number | No | No | Start time of the queried system event (13-digit timestamp), indicating the number of milliseconds since 00:00:00 on January 1, 1970. Use -1 to indicate no restriction on the start time. When used in conjunction with endTime, the intersection of both is taken. It is recommended to set a reasonable time range to optimize query performance. |
| endTime | number | No | No | End time of the queried system event (13-digit timestamp), indicating the number of milliseconds since 00:00:00 on January 1, 1970. Use -1 to indicate no restriction on the end time. When used in conjunction with beginTime, the intersection of both is taken. It is recommended to set a reasonable time range to optimize query performance. |
| maxEvents | number | No | No | Maximum number of queried system events. It is recommended to set a reasonable value to optimize query performance. |
| fromSeq<sup>10+</sup> | number | No | Yes | Start sequence number of the queried system event. The default value is -1, indicating no restriction on the start sequence number. When used in conjunction with toSeq, the intersection of both is taken. It is recommended to set a reasonable sequence range to optimize query performance. |
| toSeq<sup>10+</sup> | number | No | Yes | End sequence number of the queried system event. The default value is -1, indicating no restriction on the end sequence number. When used in conjunction with fromSeq, the intersection of both is taken. It is recommended to set a reasonable sequence range to optimize query performance. |

## QueryRule

Defines event query rules.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| domain | string | No| No| Event domain.|
| names | string[] | No| No| Array of event names. A **QueryRule** object contains multiple system event names.|
| condition<sup>10+</sup> | string | No | Yes | Additional parameter condition of the event. Format: {"version":"V1","condition":{"and":[{"param":"Parameter","op":"Operator","value":"Comparison value"}]}}.<br>param: specifies the key of the event parameter, of the string type.<br>Supported operators: =, !=, <, <=, >, and >=.<br>value: comparison value, which can be of the string, number, or other type.<br>Multiple conditions can be configured in the "and" array, and the query results take the intersection. It is recommended to avoid configuring too many complex conditions to optimize query performance. By default, no additional parameter filtering is performed when this parameter is not passed. |

## Querier

Defines an event query instance.

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| onQuery | function | No | No | Callback method used to return the queried system events (infos: [SysEventInfo](#syseventinfo)[]) => void. Triggered when system events are queried (may be called multiple times). The callback receives the queried [SysEventInfo](#syseventinfo) array to process the query result. |
| onComplete | function | No | No | Callback method used to return the query result statistics (reason: number, total: number) => void. Triggered when the query is complete (called only once). The callback receives the query result statistics: reason indicates the reason for query completion (such as query success or query timeout), and total indicates the total number of queried events. |

## hiSysEvent.query

query(queryArg: QueryArg, rules: QueryRule[], querier: Querier): void

Queries system events. Supports matching queries based on multiple query conditions such as the time range, event domain, and event name.

**Required permission**: ohos.permission.READ_DFX_SYSEVENT

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ----------------------------- | ---- | ------------------------ |
| queryArg | [QueryArg](#queryarg) | Yes  | Arguments for event query.|
| rules | [QueryRule](#queryrule)[] | Yes  | Array of event query rules.|
| querier | [Querier](#querier) | Yes  | Event query instance.|

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT.                         |
| 202      | System API is not allowed called by Non-system application.                                                                                     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200301 | The number of query rules exceeds the limit.                                                                                                    |
| 11200302 | Invalid query rule.                                                                                                                             |
| 11200303 | The number of concurrent queriers exceeds the limit.                                                                                            |
| 11200304 | The query frequency exceeds the limit.                                                                                                          |

**Example**

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo, (err: BusinessError) => {
    // Handle operations after the event is written successfully.
  });

  let queryArg: hiSysEvent.QueryArg = {
    beginTime: -1,
    endTime: -1,
    maxEvents: 5,
  };
  let queryRules: hiSysEvent.QueryRule[] = [{
    domain: "RELIABILITY",
    names: ["STACK"],
    condition: '{"version":"V1","condition":{"and":[{"param":"PID","op":"=","value":487},{"param":"PROCESS_NAME","op":"=","value":"syseventservice"}]}}'
  } as hiSysEvent.QueryRule];
  let querier: hiSysEvent.Querier = {
    onQuery: (infos: hiSysEvent.SysEventInfo[]) => {
      // Handle the queried system event infos.
    },
    onComplete: (reason: number, total: number) => {
      // Handle the end of the query.
    }
  };
  hiSysEvent.query(queryArg, queryRules, querier);
} catch (err) {
  // Catch and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

## hiSysEvent.exportSysEvents<sup>10+</sup>

exportSysEvents(queryArg: QueryArg, rules: QueryRule[]): number

Exports system events in batches and writes them as files to the fixed directory of the application sandbox (/data/storage/el2/base/cache/hiview/event/). After the call succeeds, the timestamp of the API call is returned, which can be used to locate the exported event files.

**Required permission**: ohos.permission.READ_DFX_SYSEVENT

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name  | Type                     | Mandatory| Description                                      |
| -------- | ------------------------- | ---- | ------------------------------------------ |
| queryArg | [QueryArg](#queryarg)     | Yes  | Event query parameters for the export.                  |
| rules    | [QueryRule](#queryrule)[] | Yes  | Array of event query rules for the export.|

**Return value**

| Type  | Description            |
| ------ | ---------------- |
| number | Timestamp of the API call, in milliseconds (ms). |

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT.                         |
| 202      | System API is not allowed called by Non-system application.                                                                                     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200301 | The number of query rules exceeds the limit.                                                                                                    |
| 11200302 | Invalid query rule.                                                                                                                             |
| 11200304 | The query frequency exceeds the limit.                                                                                                          |

**Example**

```ts
import { fileIo } from '@kit.CoreFileKit';
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo, (err: BusinessError) => {
    // Handle the operations after the event is written successfully.
  });

  let queryArg: hiSysEvent.QueryArg = {
    beginTime: -1,
    endTime: -1,
    maxEvents: 1,
  };
  let queryRules: hiSysEvent.QueryRule[] = [{
    domain: "RELIABILITY",
    names: ["STACK"],
  } as hiSysEvent.QueryRule];
  let time = hiSysEvent.exportSysEvents(queryArg, queryRules);
  console.info(`receive export task time is : ${time}`);

  // Wait for the file write to complete before reading (recommended to confirm by listening for file system events or polling the file size).
  setTimeout(() => {
    let eventDir = '/data/storage/el2/base/cache/hiview/event';
    let filenames = fileIo.listFileSync(eventDir);
    for (let i = 0; i < filenames.length; i++) {
      if (filenames[i].indexOf(time.toString()) != -1) {
        let res = fileIo.readTextSync(eventDir + '/' + filenames[i]);
        let events: string = JSON.parse('[' + res.slice(0, res.length - 1) + ']');
        console.info("read file end, events is :" + JSON.stringify(events));
      }
    }
  }, 10000);
} catch (err) {
  // Catch and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

## hiSysEvent.subscribe<sup>10+</sup>

subscribe(rules: QueryRule[]): number

Subscribes to real-time system events (the events must meet the constraints of low frequency or occasional occurrence). When an event occurs, it is immediately written to the fixed application sandbox directory (/data/storage/el2/base/cache/hiview/event/) in file format. It is used for real-time monitoring of key system events and generating alarms, such as performance anomaly alarms and security event monitoring. It is applicable to key events with low frequency or occasional occurrence, and is not recommended for high-frequency events.

**Required permission**: ohos.permission.READ_DFX_SYSEVENT

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Parameters**

| Name| Type                     | Mandatory| Description                                      |
| ------ | ------------------------- | ---- | ------------------------------------------ |
| rules  | [QueryRule](#queryrule)[] | Yes  | Array of event query rules for the subscription.|

**Return value**

| Type  | Description            |
| ------ | ---------------- |
| number | API call timestamp, in milliseconds (ms). |

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT.                         |
| 202      | System API is not allowed called by Non-system application.                                                                                     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200301 | The number of query rules exceeds the limit.                                                                                                    |
| 11200302 | Invalid query rule.                                                                                                                             |

**Example**

```ts
import { fileIo } from '@kit.CoreFileKit';
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let rules: hiSysEvent.QueryRule[] = [{
    domain: "RELIABILITY",
    names: ["STACK"],
  } as hiSysEvent.QueryRule,
  {
    domain: "BUNDLE_MANAGER",
    names: ["BUNDLE_UNINSTALL"],
  } as hiSysEvent.QueryRule];
  hiSysEvent.subscribe(rules);

  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo, (err: BusinessError) => {
    // Handle the operations after the event is written successfully.
  });

  // Wait for the file write to complete before reading (recommended to confirm by listening to file system events or polling the file size).
  setTimeout(() => {
    let eventDir = '/data/storage/el2/base/cache/hiview/event';
    let filenames = fileIo.listFileSync(eventDir);
    for (let i = 0; i < filenames.length; i++) {
      let res = fileIo.readTextSync(eventDir + '/' + filenames[i]);
      let events: string = JSON.parse('[' + res.slice(0, res.length - 1) + ']');
      console.info("read file end, events is :" + JSON.stringify(events));
    }
  }, 10000);
} catch (err) {
  // Catch and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

## hiSysEvent.unsubscribe<sup>10+</sup>

unsubscribe(): void

Unsubscribes from all real-time system events. After the unsubscription succeeds, real-time events will no longer be received. It is applicable to the scenario where real-time event subscription is no longer needed, and can release subscription resources and reduce resource usage.

**Required permission**: ohos.permission.READ_DFX_SYSEVENT

**System capability**: SystemCapability.HiviewDFX.HiSysEvent

**System API:** This API is a system API.

**Error codes**

For details about the following error codes, see [HiSysEvent Error Codes](errorcode-hisysevent-sys.md).

| ID| Error Message|
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission denied. An attempt was made to read system event forbidden by permission: ohos.permission.READ_DFX_SYSEVENT.                         |
| 202      | System API is not allowed called by Non-system application.                                                                                     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200305 | Unsubscription failed.                                                                                                                          |

**Example**

```ts
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let rules: hiSysEvent.QueryRule[] = [{
    domain: "RELIABILITY",
    names: ["STACK"],
  } as hiSysEvent.QueryRule,
  {
    domain: "BUNDLE_MANAGER",
    names: ["BUNDLE_UNINSTALL"],
  } as hiSysEvent.QueryRule];
  hiSysEvent.subscribe(rules);
  hiSysEvent.unsubscribe();
} catch (err) {
  // Capture and print the error message.
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

