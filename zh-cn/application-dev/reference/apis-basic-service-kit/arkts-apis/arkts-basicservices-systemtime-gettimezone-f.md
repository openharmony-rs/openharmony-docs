# getTimezone

## 导入模块

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

<a id="gettimezone"></a>
## getTimezone

```TypeScript
function getTimezone(callback: AsyncCallback<string>): void
```

获取系统时区，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getTimezone(callback:](arkts-basicservices-systemdatetime-gettimezone-f.md#gettimezone-1)

<!--Device-systemTime-function getTimezone(callback: AsyncCallback<string>): void--><!--Device-systemTime-function getTimezone(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回系统时区。具体可见[支持的系统时区](docroot://reference/apis-basic-services-kit/js-apis-system-time.md#支持的系统时区) 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getTimezone((error: BusinessError, data: string) => {
    if (error) {
      console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting timezone : ${data}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}

```


<a id="gettimezone-1"></a>
## getTimezone

```TypeScript
function getTimezone(): Promise<string>
```

获取系统时区，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getTimezone()](arkts-basicservices-systemdatetime-gettimezone-f.md#gettimezone-1)

<!--Device-systemTime-function getTimezone(): Promise<string>--><!--Device-systemTime-function getTimezone(): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回系统时区。具体可见[支持的系统时区](docroot://reference/apis-basic-services-kit/js-apis-system-time.md#支持的系统时区) 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| -1 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getTimezone().then((data: string) => {
    console.info(`Succeeded in getting timezone: ${data}`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}

```

