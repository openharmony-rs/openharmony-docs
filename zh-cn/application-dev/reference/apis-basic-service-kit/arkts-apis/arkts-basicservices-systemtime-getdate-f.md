# getDate

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## getDate

```TypeScript
function getDate(callback: AsyncCallback<Date>): void
```

获取当前系统日期，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDate](arkts-basicservices-systemdatetime-getdate-f.md#getdate-1)

<!--Device-systemTime-function getDate(callback: AsyncCallback<Date>): void--><!--Device-systemTime-function getDate(callback: AsyncCallback<Date>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Date> | 是 | 回调函数，返回当前系统日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getDate((error: BusinessError, date: Date) => {
    if (error) {
      console.info(`Failed to get date. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting date : ${date}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get date. message: ${error.message}, code: ${error.code}`);
}

```


## getDate

```TypeScript
function getDate(): Promise<Date>
```

获取当前系统日期，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDate](arkts-basicservices-systemdatetime-getdate-f.md#getdate-1)

<!--Device-systemTime-function getDate(): Promise<Date>--><!--Device-systemTime-function getDate(): Promise<Date>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Date> | Promise对象，返回当前系统日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getDate().then((date: Date) => {
    console.info(`Succeeded in getting date : ${date}`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to get date. message: ${error.message}, code: ${error.code}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get date. message: ${error.message}, code: ${error.code}`);
}

```

