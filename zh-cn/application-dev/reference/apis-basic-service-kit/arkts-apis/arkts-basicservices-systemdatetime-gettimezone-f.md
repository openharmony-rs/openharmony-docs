# getTimezone

## getTimezone

```TypeScript
function getTimezone(callback: AsyncCallback<string>): void
```

获取系统时区，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-systemDateTime-function getTimezone(callback: AsyncCallback<string>): void--><!--Device-systemDateTime-function getTimezone(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回系统时区。具体可见 支持的系统时区。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone((error: BusinessError, timezone: string) => {
    if (error) {
      console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in getting timezone: ${timezone}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone((error: BusinessError<void> | null, data: string | undefined) => {
    if (error) {
      console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in get timezone : ${data}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```


## getTimezone

```TypeScript
function getTimezone(): Promise<string>
```

获取系统时区，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-systemDateTime-function getTimezone(): Promise<string>--><!--Device-systemDateTime-function getTimezone(): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回系统时区。具体可见 支持的系统时区。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone().then((timezone: string) => {
    console.info(`Succeeded in getting timezone: ${timezone}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone().then((data: string) => {
    console.info(`Succeeded in getting timezone: ${data}`);
  }).catch((error: Error) => {
    console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```

