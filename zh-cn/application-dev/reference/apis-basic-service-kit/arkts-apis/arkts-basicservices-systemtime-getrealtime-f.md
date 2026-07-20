# getRealTime

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

<a id="getrealtime"></a>
## getRealTime

```TypeScript
function getRealTime(isNano: boolean, callback: AsyncCallback<number>): void
```

获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md#getuptime-1)

<!--Device-systemTime-function getRealTime(isNano: boolean, callback: AsyncCallback<number>): void--><!--Device-systemTime-function getRealTime(isNano: boolean, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isNano | boolean | 是 | 返回结果是否为纳秒数。<br/>- true：表示返回结果为纳秒数（ns）。 <br/>- false：表示返回结果为毫秒数（ms）。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回自系统启动以来经过的时间，包括深度睡眠时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getRealTime(true, (error: BusinessError, time: number) => {
    if (error) {
      console.info(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting real time : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
}

```


<a id="getrealtime-1"></a>
## getRealTime

```TypeScript
function getRealTime(callback: AsyncCallback<number>): void
```

获取自系统启动以来经过的时间，包括深度睡眠时间，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md#getuptime-1)

<!--Device-systemTime-function getRealTime(callback: AsyncCallback<number>): void--><!--Device-systemTime-function getRealTime(callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回自系统启动以来经过的时间（ms），包括深度睡眠时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getRealTime((error: BusinessError, time: number) => {
    if (error) {
      console.info(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting real time : ${time}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
}

```


<a id="getrealtime-2"></a>
## getRealTime

```TypeScript
function getRealTime(isNano?: boolean): Promise<number>
```

获取自系统启动以来经过的时间，包括深度睡眠时间，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md#getuptime-1)

<!--Device-systemTime-function getRealTime(isNano?: boolean): Promise<number>--><!--Device-systemTime-function getRealTime(isNano?: boolean): Promise<number>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isNano | boolean | 否 | 返回结果是否为纳秒数，默认值为false。<br/>默认值为false。<br/>- true：表示返回结果为纳秒数（ns）。 <br/>- false：表示返回结果为毫秒数（ms）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回自系统启动以来经过的时间，包括深度睡眠时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getRealTime().then((time: number) => {
    console.info(`Succeeded in getting real time : ${time}`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
}

```

