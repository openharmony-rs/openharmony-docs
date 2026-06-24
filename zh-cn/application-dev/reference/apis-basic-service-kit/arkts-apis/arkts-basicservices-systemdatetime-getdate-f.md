# getDate

## getDate

```TypeScript
function getDate(callback: AsyncCallback<Date>): void
```

获取当前系统日期，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** new

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Date&gt; | 是 | 回调函数，返回当前系统日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. System error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getDate((error: BusinessError, date: Date) => {
    if (error) {
      console.error(`Failed to get date. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting date : ${date}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get date. message: ${error.message}, code: ${error.code}`);
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

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Date&gt; | Promise对象，返回当前系统日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. System error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getDate().then((date: Date) => {
    console.info(`Succeeded in getting date : ${date}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get date. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get date. message: ${error.message}, code: ${error.code}`);
}

```

