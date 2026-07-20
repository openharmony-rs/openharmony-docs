# setDate（系统接口）

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

<a id="setdate"></a>
## setDate

```TypeScript
function setDate(date: Date, callback: AsyncCallback<void>): void
```

设置系统日期，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [setTime(time:](arkts-basicservices-systemdatetime-settime-f-sys.md#settime-1)

**需要权限：** ohos.permission.SET_TIME

<!--Device-systemDateTime-function setDate(date: Date, callback: AsyncCallback<void>): void--><!--Device-systemDateTime-function setDate(date: Date, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 目标日期，且必须>0。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types.<br> 3. Parameter verification failed; |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date();
try {
  systemDateTime.setDate(date, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in setting date.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="setdate-1"></a>
## setDate

```TypeScript
function setDate(date: Date): Promise<void>
```

设置系统日期，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [setTime(time:](arkts-basicservices-systemdatetime-settime-f-sys.md#settime-1)

**需要权限：** ohos.permission.SET_TIME

<!--Device-systemDateTime-function setDate(date: Date): Promise<void>--><!--Device-systemDateTime-function setDate(date: Date): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 目标日期，且必须>0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types.<br> 3. Parameter verification failed; |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date(); 
try {
  systemDateTime.setDate(date).then(() => {
    console.info(`Succeeded in setting date.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set date. Code: ${error.code}, message: ${error.message}`);
}

```

