# startTimer（系统接口）

## startTimer

```TypeScript
function startTimer(timer: number, triggerTime: number, callback: AsyncCallback<void>): void
```

开启定时器，使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timer | number | 是 | 定时器的ID。 |
| triggerTime | number | 是 | 定时器的触发时间，单位：毫秒。<br/>若定时器类型包含了TIMER_TYPE_REALTIME，该triggerTime应为系统启动时间，建议通过<br/>[systemDateTime.getUptime(STARTUP)](arkts-basicservices-systemdatetime-getuptime-f.md#getUptime-1)获取；<br/>若定时器类型不包含<br/>TIMER_TYPE_REALTIME，该triggerTime应为墙上时间，建议通过<br/>[systemDateTime.getTime()](arkts-basicservices-systemdatetime-gettime-f.md#getTime-1)获取。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
}
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to start timer. message: ${error.message}, code: ${error.code}`);
        return;
      }
      console.info(`Succeeded in starting timer.`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
}

```


## startTimer

```TypeScript
function startTimer(timer: number, triggerTime: number): Promise<void>
```

开启定时器，使用Promise进行异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timer | number | 是 | 定时器的ID。 |
| triggerTime | number | 是 | 定时器的触发时间，单位：毫秒。<br/>若定时器类型包含了TIMER_TYPE_REALTIME，该triggerTime应为系统启动时间，建议通过<br/>[systemDateTime.getUptime(STARTUP)](arkts-basicservices-systemdatetime-getuptime-f.md#getUptime-1)获取；<br/>若定时器类型不包含<br/>TIMER_TYPE_REALTIME，该triggerTime应为墙上时间，建议通过<br/>[systemDateTime.getTime()](arkts-basicservices-systemdatetime-gettime-f.md#getTime-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
}
let triggerTime: number = new Date().getTime();
triggerTime += 3000;

try {
  systemTimer.createTimer(options).then((timerId: number) => {
    systemTimer.startTimer(timerId, triggerTime).then(() => {
      console.info(`Succeeded in starting timer.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to start timer. message: ${error.message}, code: ${error.code}`);
    });
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to create timer. message: ${error.message}, code: ${error.code}`);
}

```

