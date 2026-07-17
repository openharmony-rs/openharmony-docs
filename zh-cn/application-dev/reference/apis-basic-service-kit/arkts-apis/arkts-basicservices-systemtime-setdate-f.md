# setDate

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## setDate

```TypeScript
function setDate(date: Date, callback: AsyncCallback<void>): void
```

设置系统日期，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md#setdate-1)

**需要权限：** ohos.permission.SET_TIME

<!--Device-systemTime-function setDate(date: Date, callback: AsyncCallback<void>): void--><!--Device-systemTime-function setDate(date: Date, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 目标日期。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date();
try {
  systemTime.setDate(date, (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting date.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
}

```


## setDate

```TypeScript
function setDate(date: Date): Promise<void>
```

设置系统日期，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md#setdate-1)

**需要权限：** ohos.permission.SET_TIME

<!--Device-systemTime-function setDate(date: Date): Promise<void>--><!--Device-systemTime-function setDate(date: Date): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 目标日期。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date(); 
try {
  systemTime.setDate(date).then(() => {
    console.info(`Succeeded in setting date.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
}

```

