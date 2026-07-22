# write（系统接口）

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## write

```TypeScript
function write(info: SysEventInfo): Promise<void>
```

系统事件打点方法，接收[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)类型的对象作为事件参数，使用promise方式作为异步回调。

**起始版本：** 9

<!--Device-hiSysEvent-function write(info: SysEventInfo): Promise<void>--><!--Device-hiSysEvent-function write(info: SysEventInfo): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | 是 | 系统事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise实例，可以在其then()、catch()方法中分别对系统事件写入成功、写入异常的回调进行处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [11200001](../errorcode-hisysevent-sys.md#11200001-非法的事件领域) | Invalid event domain. |
| [11200002](../errorcode-hisysevent-sys.md#11200002-非法的事件名称) | Invalid event name. |
| [11200003](../errorcode-hisysevent-sys.md#11200003-环境异常) | Abnormal environment. |
| [11200004](../errorcode-hisysevent-sys.md#11200004-事件长度超过限制) | The event length exceeds the limit. |
| [11200051](../errorcode-hisysevent-sys.md#11200051-非法的事件参数) | Invalid event parameter. |
| [11200052](../errorcode-hisysevent-sys.md#11200052-字符串类型的事件参数值的长度超过限制) | The size of the event parameter of the string type exceeds the limit. |
| [11200053](../errorcode-hisysevent-sys.md#11200053-事件参数的数量超过限制) | The number of event parameters exceeds the limit. |
| [11200054](../errorcode-hisysevent-sys.md#11200054-数组类型的事件参数值的长度超过限制) | The number of event parameters of the array type exceeds the limit. |

**示例：**

```TypeScript
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
  // 使用Promise方式写入系统事件，then中处理成功事件，catch中处理错误
  hiSysEvent.write(eventInfo).then(
    () => {
      // 处理事件写入成功后的操作
    }
  ).catch(
    (err: BusinessError) => {
      // 捕获并打印错误信息
      console.error(`error code: ${err.code}, error msg: ${err.message}`);
    }
  );
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}

```


## write

```TypeScript
function write(info: SysEventInfo, callback: AsyncCallback<void>): void
```

系统事件打点方法，接收[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)类型的对象作为事件参数，使用callback方式作为异步回调。

**起始版本：** 9

<!--Device-hiSysEvent-function write(info: SysEventInfo, callback: AsyncCallback<void>): void--><!--Device-hiSysEvent-function write(info: SysEventInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | 是 | 系统事件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，可以在回调函数中处理接口返回值。<br/>- 0表示事件校验成功，事件正常异步写入事件文件；<br/>- 正值表示事件打点存在异常，但可以正常写入；<br/>- 负值表示事件打点失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [11200001](../errorcode-hisysevent-sys.md#11200001-非法的事件领域) | Invalid event domain. |
| [11200002](../errorcode-hisysevent-sys.md#11200002-非法的事件名称) | Invalid event name. |
| [11200003](../errorcode-hisysevent-sys.md#11200003-环境异常) | Abnormal environment. |
| [11200004](../errorcode-hisysevent-sys.md#11200004-事件长度超过限制) | The event length exceeds the limit. |
| [11200051](../errorcode-hisysevent-sys.md#11200051-非法的事件参数) | Invalid event parameter. |
| [11200052](../errorcode-hisysevent-sys.md#11200052-字符串类型的事件参数值的长度超过限制) | The size of the event parameter of the string type exceeds the limit. |
| [11200053](../errorcode-hisysevent-sys.md#11200053-事件参数的数量超过限制) | The number of event parameters exceeds the limit. |
| [11200054](../errorcode-hisysevent-sys.md#11200054-数组类型的事件参数值的长度超过限制) | The number of event parameters of the array type exceeds the limit. |

**示例：**

```TypeScript
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
    // 处理事件写入成功后的操作
  });
} catch (err) {
  // 捕获并打印错误信息
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}

```

