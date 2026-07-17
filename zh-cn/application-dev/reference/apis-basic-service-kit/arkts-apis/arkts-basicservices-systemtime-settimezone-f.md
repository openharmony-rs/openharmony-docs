# setTimezone

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## setTimezone

```TypeScript
function setTimezone(timezone: string, callback: AsyncCallback<void>): void
```

设置系统时区，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md#settimezone-1)

**需要权限：** ohos.permission.SET_TIME_ZONE

<!--Device-systemTime-function setTimezone(timezone: string, callback: AsyncCallback<void>): void--><!--Device-systemTime-function setTimezone(timezone: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timezone | string | 是 | 系统时区。具体可见[支持的系统时区](../../../../reference/apis-basic-services-kit/js-apis-system-time.md#支持的系统时区) 。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.setTimezone('Asia/Shanghai', (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting timezone.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
}

```


## setTimezone

```TypeScript
function setTimezone(timezone: string): Promise<void>
```

使用Promise异步回调设置系统时区。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md#settimezone-1)

**需要权限：** ohos.permission.SET_TIME_ZONE

<!--Device-systemTime-function setTimezone(timezone: string): Promise<void>--><!--Device-systemTime-function setTimezone(timezone: string): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timezone | string | 是 | 系统时区。具体可见[支持的系统时区](../../../../reference/apis-basic-services-kit/js-apis-system-time.md#支持的系统时区) 。 |

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

try {
  systemTime.setTimezone('Asia/Shanghai').then(() => {
    console.info(`Succeeded in setting timezone.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
}

```

