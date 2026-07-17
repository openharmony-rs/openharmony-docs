# createTimer（系统接口）

## 导入模块

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## createTimer

```TypeScript
function createTimer(options: TimerOptions, callback: AsyncCallback<number>): void
```

创建定时器，使用callback异步回调。

> **注意：**  
>  
> 需与[systemTimer.destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md#destroytimer-1)结合使用，否则会造  
> 成内存泄漏

**起始版本：** 7

<!--Device-systemTimer-function createTimer(options: TimerOptions, callback: AsyncCallback<long>): void--><!--Device-systemTimer-function createTimer(options: TimerOptions, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimerOptions](arkts-basicservices-systemtimer-timeroptions-i-sys.md) | 是 | 创建系统定时器的初始化选项，包括定时器类型、是否循环触发、间隔时间、WantAgent通知机制等。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数，返回定时器的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types.<br> 3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat: false
};
try {
  systemTimer.createTimer(options, (error: BusinessError, timerId: number) => {
    if (error) {
      console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
}

```


## createTimer

```TypeScript
function createTimer(options: TimerOptions): Promise<number>
```

创建定时器，使用Promise异步回调返回定时器的ID。

> **注意：**  
>  
> 需与[systemTimer.destroyTimer](arkts-basicservices-systemtimer-destroytimer-f-sys.md#destroytimer-1)结合使用，否则会造  
> 成内存泄漏

**起始版本：** 7

<!--Device-systemTimer-function createTimer(options: TimerOptions): Promise<long>--><!--Device-systemTimer-function createTimer(options: TimerOptions): Promise<long>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimerOptions](arkts-basicservices-systemtimer-timeroptions-i-sys.md) | 是 | 创建系统定时器的初始化选项，包括定时器类型、是否循环触发、间隔时间、WantAgent通知机制等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回定时器的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types.<br> 3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: systemTimer.TimerOptions = {
  type: systemTimer.TIMER_TYPE_REALTIME,
  repeat:false
};
try {
  systemTimer.createTimer(options).then((timerId: number) => {
    console.info(`Succeeded in creating timer. timerId: ${timerId}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create timer. Code: ${error.code}, message: ${error.message}`);
}

```

