# getNtpTime（系统接口）

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getNtpTime

```TypeScript
function getNtpTime(): number
```

使用同步方式获取基于上次更新的NTP时间所计算出的真实时间。

**起始版本：** 14

<!--Device-systemDateTime-function getNtpTime(): long--><!--Device-systemDateTime-function getNtpTime(): long-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 基于上次更新的NTP时间所计算出的Unix纪元时间(ms)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [13000002](../../apis-basic-services-kit/errorcode-time.md#13000002-未更新ntp时间) | updateNtpTime() is not called successfully. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getNtpTime();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get ntp time. Code: ${error.code}, message: ${error.message}`);
}

```

