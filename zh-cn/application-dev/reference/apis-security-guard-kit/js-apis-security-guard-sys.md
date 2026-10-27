# @ohos.security.securityGuard (设备风险管理平台)(系统接口)
<!--Kit: Security Guard Kit-->
<!--Subsystem: Security-->
<!--Owner: @sunyibo-->
<!--Designer: @shipengfei-->
<!--Tester: @songjinke-->
<!--Adviser: @zengyawen-->

本模块提供设备风险管理能力，包括安全事件采集、上报、查询与订阅，安全模型检测结果获取、策略文件更新，以及阻断服务提供者接入阻断框架进行事件阻断决策。基于事件数据可分析设备运行风险。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块为系统接口。
> - 从 API version 26.1.0 开始，新增阻断服务提供者接入接口，包括 `createAuthProvider`、`destroyAuthProvider`、`AuthProvider.requestAuthResult` 及相关类型。


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

### onComplete

onComplete: () => void

查询完成时触发。触发后查询会话结束，无需再保留querier对象。

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

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
- 订阅成功后需在适当时机调用[off](#securityguardoff)()取消订阅。

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


## AuthStrategy

表示阻断策略的枚举。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| ALLOW | 0 | 允许，放行事件。 |
| DENY | 1 | 拒绝，阻断事件。 |
| TIMEOUT | 2 | 超时，客户端响应超时且默认策略为放行时记录此结果。 |

## AuthEventInfo

阻断事件信息。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| eventId | number | 否 | 否 | 事件类型ID。 |
| version | string | 否 | 否 | 事件版本号。 |
| content | string | 否 | 否 | 事件内容，JSON字符串格式。 |
| clientStatus | Array&lt;[AuthClientStatus](#authclientstatus)&gt; | 否 | 是 | 客户端会话状态列表，用于标记降级客户端。降级的客户端仅上报通知，不参与从严聚合。 |

## AuthClientStatus

客户端会话状态，标记单个客户端是否降级。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| clientId | string | 否 | 否 | 客户端会话唯一标识。 |
| isDegraded | boolean | 否 | 否 | 事件是否降级。true表示降级，降级的事件仅上报通知，不需要接收阻断结果，不参与从严聚合；false表示未降级，正常参与阻断决策与从严聚合。 |

## AuthClientInfo

客户端会话信息，由框架通过 [onClientStatusChanged](#onclientstatuschanged) 回调下发给阻断服务提供者。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| clientId | string | 否 | 否 | 客户端会话唯一标识。 |
| bundleName | string | 否 | 否 | 应用Bundle名称。 |
| subscribedEvents | Array&lt;number&gt; | 否 | 否 | 客户端订阅的事件类型ID列表。阻断服务提供者可据此过滤关心的事件。 |
| defaultTimeoutStrategy | [AuthStrategy](#authstrategy) | 否 | 否 | 客户端响应超时时的默认阻断策略。 |
| defaultTimeoutMs | number | 否 | 否 | 客户端响应超时时间，单位毫秒。当前默认设置为400。 |

## ClientAuthResult

单个客户端的阻断结果。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| clientId | string | 否 | 否 | 客户端会话唯一标识。 |
| authStrategy | [AuthStrategy](#authstrategy) | 否 | 否 | 该客户端的阻断策略。 |

## AuthResult

所有客户端阻断结果。

从严策略：任一客户端返回 DENY 即阻断，全部客户端返回 ALLOW 才放行。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| mergedAuthStrategy | [AuthStrategy](#authstrategy) | 否 | 否 | 所有客户端聚合后的阻断策略。 |
| clientAuthResult | Array&lt;[ClientAuthResult](#clientauthresult)&gt; | 否 | 否 | 各客户端的阻断结果列表。 |

## AuthProviderCallback

阻断服务提供者回调接口，在调用 [createAuthProvider](#securityguardcreateauthprovider) 时传入。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

### onClientStatusChanged

onClientStatusChanged: (clientInfos: Array&lt;AuthClientInfo&gt;) => void

客户端会话状态变更时触发。[createAuthProvider](#securityguardcreateauthprovider) 成功后会立即触发一次，下发当前全量客户端列表；后续客户端创建、销毁或订阅变更时再次触发。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| clientInfos | Array&lt;[AuthClientInfo](#authclientinfo)&gt; | 是 | 全量客户端会话信息列表。 |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// onClientStatusChanged 作为 createAuthProvider 的回调传入，此处仅演示回调内部处理逻辑
let callback: securityGuard.AuthProviderCallback = {
  onClientStatusChanged: (clientInfos: Array<securityGuard.AuthClientInfo>) => {
    hilog.info(0x0000, 'testTag', 'clientCount %{public}d', clientInfos.length);
    for (let info of clientInfos) {
      hilog.info(0x0000, 'testTag', 'clientId %{public}s, events %{public}d',
        info.clientId, info.subscribedEvents.length);
    }
  }
};
```

## AuthProvider

阻断服务提供者类，由 [createAuthProvider](#securityguardcreateauthprovider) 工厂函数创建。通过该类实例可请求事件的阻断结果。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

### requestAuthResult

requestAuthResult(event: AuthEventInfo): Promise&lt;AuthResult&gt;

请求事件的阻断结果。使用Promise异步回调。

- 单个Provider并发请求上限为128，超限返回27000004。
- 框架侧超时时间为400毫秒，超时后按各客户端默认策略聚合并resolve Promise。
- 从严聚合：任一客户端阻断即阻断，全部客户端放行才放行。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.AUTH_SERVICE_ACCESS

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| event | [AuthEventInfo](#autheventinfo) | 是 | 阻断事件信息。eventId、version、content必填。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise&lt;[AuthResult](#authresult)&gt; | Promise对象，成功时返回阻断结果，失败时抛出BusinessError。 |

**错误码：**

下表仅列出本接口特有的错误码，通用错误码请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 27000001 | internal system error. |
| 27000004 | concurrent request count has reached the upper limit. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// provider 由 createAuthProvider 创建，此处假设已获取
let provider: securityGuard.AuthProvider;

async function requestAuthResult(): Promise<void> {
  let eventInfo: securityGuard.AuthEventInfo = {
    eventId: 1011015004,
    version: '1.0',
    content: '{"status":0}'
  };
  try {
    let result: securityGuard.AuthResult = await provider.requestAuthResult(eventInfo);
    hilog.info(0x0000, 'testTag', 'mergedStrategy %{public}d, clientCount %{public}d',
      result.mergedAuthStrategy, result.clientAuthResult.length);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
  }
}
```

## securityGuard.createAuthProvider

createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider

创建阻断服务提供者会话。同一进程最多1个Provider实例，全局最多16个。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.AUTH_SERVICE_ACCESS

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| callback | [AuthProviderCallback](#authprovidercallback) | 是 | 阻断服务提供者回调，接收客户端状态变更通知。 |
| serviceId | string | 是 | 服务标识。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [AuthProvider](#authprovider) | 阻断服务提供者实例。 |

**错误码：**

下表仅列出本接口特有的错误码，通用错误码请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 27000001 | internal system error. |
| 27000002 | Provider count of the current process has reached the upper limit. |
| 27000003 | Global provider count has reached the upper limit. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let provider: securityGuard.AuthProvider;

try {
  provider = securityGuard.createAuthProvider(
    {
      onClientStatusChanged: (clientInfos: Array<securityGuard.AuthClientInfo>) => {
        hilog.info(0x0000, 'testTag', 'clientCount %{public}d', clientInfos.length);
        for (let info of clientInfos) {
          hilog.info(0x0000, 'testTag', 'clientId %{public}s, events %{public}d',
            info.clientId, info.subscribedEvents.length);
        }
      }
    },
    'myAuthService'
  );
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```

## securityGuard.destroyAuthProvider

destroyAuthProvider(provider: AuthProvider): void

销毁阻断服务提供者会话。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.AUTH_SERVICE_ACCESS

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| provider | [AuthProvider](#authprovider) | 是 | 要销毁的阻断服务提供者实例。销毁后不可再用。 |

**错误码：**

下表仅列出本接口特有的错误码，通用错误码请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | check permission fail |
| 202 | non-system application uses the system API |
| 27000001 | internal system error. |

**示例：**

```ts
import { securityGuard } from '@kit.SecurityGuardKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// provider 由 createAuthProvider 创建，此处假设已获取
let provider: securityGuard.AuthProvider;

try {
  securityGuard.destroyAuthProvider(provider);
  hilog.info(0x0000, 'testTag', 'destroy provider success');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode %{public}d, errorMessage %{public}s', e.code, e.message);
}
```
