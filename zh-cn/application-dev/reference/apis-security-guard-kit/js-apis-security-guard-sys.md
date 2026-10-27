# @ohos.security.securityGuard (设备风险管理平台)(系统接口)
<!--Kit: Security Guard Kit-->
<!--Subsystem: Security-->
<!--Owner: @sunyibo-->
<!--Designer: @shipengfei-->
<!--Tester: @songjinke-->
<!--Adviser: @zengyawen-->

本模块提供设备风险管理能力，包括安全事件采集、上报、查询与订阅，以及安全模型检测结果获取、策略文件更新。基于事件数据可分析设备运行风险。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块为系统接口。


## 导入模块

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
```

## SecurityEvent

安全事件信息，包含事件ID、版本、内容和时间戳。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| eventId | number | 否 | 否 | 安全事件ID。 |
| version | string | 否 | 否 | 事件版本。不同版本对应不同数据格式。最大长度50字节（不含结束符）。 |
| content | string | 否 | 否 | 事件内容。上报时最大长度10240字节（不含结束符）。 |
| timestamp | string | 否 | 是 | 事件时间戳，格式为YYYYMMDDHHMMSS（14位数字）。查询结果中会返回该字段；订阅回调中不返回。 |

## SecurityEventRule

查询安全事件的过滤规则。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| eventId | number | 否 | 否 | 待查询的安全事件ID。 |
| beginTime | string | 否 | 是 | 查询起始时间，格式为YYYYMMDDHHMMSS（14位数字）。 |
| endTime | string | 否 | 是 | 查询结束时间，格式为YYYYMMDDHHMMSS（14位数字）。若同时传入beginTime和endTime，则beginTime不能大于endTime。 |
| param | string | 否 | 是 | 查询附加条件。最大长度2000字节（不含结束符）。 |

## Querier

查询安全事件的回调对象。查询过程中按批次回调onQuery()，全部完成后回调onComplete()，失败时回调onError()。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

### onQuery

onQuery: (events: Array\<SecurityEvent\>) => void

查询到一批安全事件时触发。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| events | Array\<[SecurityEvent](#securityevent)\> | 是 | 本批次查询到的安全事件列表。 |

**示例：**
请参考[onError接口](#onerror)的示例。

### onComplete

onComplete: () => void

查询完成时触发。触发后查询会话结束，无需再保留querier对象。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**示例：**
请参考[onError接口](#onerror)的示例。

### onError

onError: (message: string) => void

查询失败时触发。触发后查询会话结束。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| message | string | 是 | 错误信息，由系统在查询失败时填入。 |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let querier: securityGuard.Querier = {
  onQuery: (events: Array<securityGuard.SecurityEvent>) => {
    hilog.info(0x0000, 'testTag', 'onQuery size %{public}d', events.length);
  },
  onComplete: () => {
    hilog.info(0x0000, 'testTag', 'query complete');
  },
  onError: (message: string) => {
    hilog.error(0x0000, 'testTag', 'query error %{public}s', message);
  }
};
```

## CollectorRule

启动或停止安全事件采集器的规则。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| eventId | number | 否 | 否 | 采集的安全事件ID。取值需为设备风险管理平台已定义的事件ID。 |
| param | string | 否 | 是 | 采集附加参数。最大长度2000字节（不含结束符）。 |

## ModelRule

请求安全模型检测结果的规则。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| modelName | string | 否 | 否 | 安全模型名称。最大长度64字节（不含结束符）。<br>当前支持取值如下：<br>SecurityGuard_JailbreakCheck：越狱/Root检测模型。<br>SecurityGuard_IntegrityCheck：设备完整性检测模型。<br>SecurityGuard_SimulatorCheck：物理真机/模拟器检测模型。<br>SecurityGuard_RiskFactorCheck：安全风险因子检测模型。<br>SecurityGuard_WifiCheck：WLAN风险检测模型。<br>传入其余值将抛出401错误码。|
| param | string | 否 | 是 | 模型附加参数。最大长度900字节（不含结束符）。 |

## ModelResult

安全模型检测的结果。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| result | string | 否 | 否 | 模型检测结果。 |

## SecurityEventInfo

订阅或取消订阅安全事件时指定的事件信息。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| eventId | number | 否 | 否 | 安全事件ID。 |

## PolicyFile

策略文件信息，用于更新安全策略。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| name | string | 否 | 否 | 策略文件名。最大长度64字节（不含结束符）。 |
| fd | number | 否 | 否 | 策略文件描述符。 |

## securityGuard.startSecurityEventCollector

startSecurityEventCollector(rule: CollectorRule): void

启动安全事件采集器。

**需要权限：** ohos.permission.QUERY_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| rule | [CollectorRule](#collectorrule) | 是 | 采集规则。param为可选。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  // 按事件ID启动采集，持续到主动停止
  securityGuard.startSecurityEventCollector({ eventId: 1011015004 });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.stopSecurityEventCollector

stopSecurityEventCollector(rule: CollectorRule): void

停止安全事件采集器。

**需要权限：** ohos.permission.QUERY_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| rule | [CollectorRule](#collectorrule) | 是 | 采集规则。eventId需与启动采集时保持一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  securityGuard.stopSecurityEventCollector({ eventId: 1011015004 });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.querySecurityEvent

querySecurityEvent(rules: Array\<SecurityEventRule\>, querier: Querier): void

按规则查询已采集的安全事件。查询结果通过querier异步回调返回。

- rules必须为对象数组，不能为null或undefined。
- querier不能为null或undefined，且需实现onQuery、onComplete、onError。
- beginTime、endTime若传入，必须为14位数字字符串YYYYMMDDHHMMSS。

**需要权限：** ohos.permission.QUERY_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| rules | Array\<[SecurityEventRule](#securityeventrule)\> | 是 | 查询规则列表。 |
| querier | [Querier](#querier) | 是 | 接收查询结果的回调对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let querier: securityGuard.Querier = {
    onQuery: (events: Array<securityGuard.SecurityEvent>) => {
      hilog.info(0x0000, 'testTag', 'onQuery size %{public}d', events.length);
    },
    onComplete: () => {
      hilog.info(0x0000, 'testTag', 'query complete');
    },
    onError: (message: string) => {
      hilog.error(0x0000, 'testTag', 'query error %{public}s', message);
    }
  };
  securityGuard.querySecurityEvent(
    [{ eventId: 1011015004, beginTime: '20240101000000', endTime: '20241231235959' }],
    querier
  );
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.reportSecurityEvent

reportSecurityEvent(securityEvent: SecurityEvent): void

向设备风险管理平台上报安全事件。上报内容需包含eventId、version、content。

**需要权限：** ohos.permission.REPORT_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| securityEvent | [SecurityEvent](#securityevent) | 是 | 待上报的安全事件。eventId、version、content必填。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let event: securityGuard.SecurityEvent = {
    eventId: 1011015004,
    version: '1.0',
    content: '{"status":0}'
  };
  securityGuard.reportSecurityEvent(event);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.on('securityEventOccur')

on(type: 'securityEventOccur', securityEventInfo: SecurityEventInfo, callback: Callback\<SecurityEvent\>): void

订阅指定安全事件。使用callback异步回调。

- type必须为字符串`'securityEventOccur'`。
- 参数个数必须为3个。
- 同一callback重复订阅会被忽略，不会抛错。
- 订阅成功后需在适当时机调用[off](#securityguardoffsecurityeventoccur)()取消订阅。

**需要权限：** ohos.permission.QUERY_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| type | 'securityEventOccur' | 是 | 订阅类型，固定为securityEventOccur。 |
| securityEventInfo | [SecurityEventInfo](#securityeventinfo) | 是 | 订阅的事件信息，必须包含eventId。 |
| callback | Callback\<[SecurityEvent](#securityevent)\> | 是 | 回调函数，返回订阅的安全事件，包含eventId、version、content。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Callback } from '@ohos.base';

let callback: Callback<securityGuard.SecurityEvent> = (event: securityGuard.SecurityEvent) => {
  hilog.info(0x0000, 'testTag', 'eventId %{public}d, version %{public}s, content %{public}s',
    event.eventId, event.version, event.content);
};

try {
  securityGuard.on('securityEventOccur', { eventId: 1011015004 }, callback);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.off('securityEventOccur')

off(type: 'securityEventOccur', securityEventInfo: SecurityEventInfo, callback?: Callback\<SecurityEvent\>): void

取消订阅指定安全事件。

- type必须为字符串`'securityEventOccur'`。
- 参数个数必须为2个或3个。
- 传入callback时，仅取消该callback对应的订阅。
- 不传入callback时，取消该eventId下当前环境中的全部订阅。

**需要权限：** ohos.permission.QUERY_SECURITY_EVENT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| type | 'securityEventOccur' | 是 | 订阅类型，固定为securityEventOccur。 |
| securityEventInfo | [SecurityEventInfo](#securityeventinfo) | 是 | 取消订阅的事件信息，必须包含eventId。 |
| callback | Callback\<[SecurityEvent](#securityevent)\> | 否 | 与on时相同的回调函数。不传则取消该eventId的全部订阅。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Callback } from '@ohos.base';

let callback: Callback<securityGuard.SecurityEvent> = (event: securityGuard.SecurityEvent) => {
  hilog.info(0x0000, 'testTag', 'eventId %{public}d', event.eventId);
};

try {
  securityGuard.on('securityEventOccur', { eventId: 1011015004 }, callback);
  // 取消指定callback的订阅
  securityGuard.off('securityEventOccur', { eventId: 1011015004 }, callback);
  // 取消该eventId下全部订阅
  securityGuard.off('securityEventOccur', { eventId: 1011015004 });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.getModelResult

getModelResult(rule: ModelRule): Promise\<ModelResult\>

请求安全模型检测结果，超时时间为15000毫秒。使用Promise异步回调。

**需要权限：** ohos.permission.QUERY_SECURITY_MODEL_RESULT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| rule | [ModelRule](#modelrule) | 是 | 模型规则。modelName必填，且必须为支持的模型名称；param可选。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[ModelResult](#modelresult)\> | Promise对象，成功时返回模型检测结果，失败时抛出BusinessError。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  securityGuard.getModelResult({ modelName: 'SecurityGuard_JailbreakCheck' })
    .then((modelResult: securityGuard.ModelResult) => {
      hilog.info(0x0000, 'testTag', 'result %{public}s', modelResult.result);
    })
    .catch((error: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', error.code, error.message);
    });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.updatePolicyFile

updatePolicyFile(policyFile: PolicyFile): Promise\<void\>

更新安全策略文件。使用Promise异步回调。

**需要权限：** ohos.permission.MANAGE_SECURITY_GUARD_CONFIG

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| policyFile | [PolicyFile](#policyfile) | 是 | 策略文件信息name、fd必填，且传入的文件描述符及文件名为打开状态。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<void\> | Promise对象，更新成功时resolve，失败时reject并返回BusinessError。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 401 | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { fileIo } from '@kit.CoreFileKit';

async function updatePolicy(): Promise<void> {
  let file = fileIo.openSync('/data/storage/el2/base/haps/entry/files/policy.cfg', fileIo.OpenMode.READ_ONLY);
  try {
    await securityGuard.updatePolicyFile({ name: 'policy.cfg', fd: file.fd });
    hilog.info(0x0000, 'testTag', 'update policy success');
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
  } finally {
    fileIo.closeSync(file);
  }
}
```
