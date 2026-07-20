# getUptime

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

<a id="getuptime"></a>
## getUptime

```TypeScript
function getUptime(timeType: TimeType, isNanoseconds?: boolean): number
```

使用同步方式获取自系统启动以来经过的时间。

**起始版本：** 10

<!--Device-systemDateTime-function getUptime(timeType: TimeType, isNanoseconds?: boolean): long--><!--Device-systemDateTime-function getUptime(timeType: TimeType, isNanoseconds?: boolean): long-End-->

**系统能力：** SystemCapability.MiscServices.Time

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeType | [TimeType](arkts-basicservices-systemdatetime-timetype-e.md) | 是 | 获取时间的类型，仅能为`STARTUP`或者`ACTIVE`。 |
| isNanoseconds | boolean | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 自系统启动以来经过的时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types.<br> 3. Parameter verification failed. This error code was added due to missing issues.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getUptime(systemDateTime.TimeType.ACTIVE, false);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get uptime. Code: ${error.code}, message: ${error.message}`);
}

```

