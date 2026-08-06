# getTimezoneSync

## getTimezoneSync

```TypeScript
function getTimezoneSync(): string
```

获取系统时区，使用同步方式。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-systemDateTime-function getTimezoneSync(): string--><!--Device-systemDateTime-function getTimezoneSync(): string-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回系统时区。具体可见\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let timezone: string = systemDateTime.getTimezoneSync();
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let timezone: string = systemDateTime.getTimezoneSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get timezone. Code: ${error.code}, message: ${error.message}`);
}
```

