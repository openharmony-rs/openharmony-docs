# getTime

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getTime

```TypeScript
function getTime(isNanoseconds?: boolean): number
```

使用同步方式获取自Unix纪元以来到当前系统时间所经过的时间。

**起始版本：** 10

<!--Device-systemDateTime-function getTime(isNanoseconds?: boolean): long--><!--Device-systemDateTime-function getTime(isNanoseconds?: boolean): long-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isNanoseconds | boolean | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 自Unix纪元以来到当前系统时间所经过的时间。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getTime(true);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get time. Code: ${error.code}, message: ${error.message}`);
}

```

