# getTimezoneSync

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

<a id="gettimezonesync"></a>
## getTimezoneSync

```TypeScript
function getTimezoneSync(): string
```

获取系统时区，使用同步方式。

**起始版本：** 10

<!--Device-systemDateTime-function getTimezoneSync(): string--><!--Device-systemDateTime-function getTimezoneSync(): string-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回系统时区。具体可见[支持的系统时区](docroot://reference/apis-basic-services-kit/js-apis-date-time.md#支持的系统时区)。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let timezone: string = systemDateTime.getTimezoneSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}

```

