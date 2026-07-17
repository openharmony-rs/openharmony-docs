# getDate

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getDate

```TypeScript
function getDate(callback: AsyncCallback<Date>): void
```

获取当前系统日期，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** new

<!--Device-systemDateTime-function getDate(callback: AsyncCallback<Date>): void--><!--Device-systemDateTime-function getDate(callback: AsyncCallback<Date>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Date> | 是 | 回调函数，返回当前系统日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. System error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getDate((error: BusinessError, date: Date) => {
    if (error) {
      console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting date : ${date}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
}

```


## getDate

```TypeScript
function getDate(): Promise<Date>
```

获取当前系统日期，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** new

<!--Device-systemDateTime-function getDate(): Promise<Date>--><!--Device-systemDateTime-function getDate(): Promise<Date>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Date> | Promise对象，返回当前系统日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. System error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getDate().then((date: Date) => {
    console.info(`Succeeded in getting date : ${date}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get date. Code: ${error.code}, message: ${error.message}`);
}

```

