# getTimezoneSync

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getTimezoneSync

```TypeScript
function getTimezoneSync(): string
```

获取系统时区，使用同步方式。

**起始版本：** 23

<!--Device-systemDateTime-function getTimezoneSync(): string--><!--Device-systemDateTime-function getTimezoneSync(): string-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回系统时区。具体可见支持的系统时区。 |

**示例**

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

