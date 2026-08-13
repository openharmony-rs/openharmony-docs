# setTimezone（系统接口）

## setTimezone

```TypeScript
function setTimezone(timezone: string, callback: AsyncCallback<void>): void
```

设置系统时区，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TIME_ZONE

<!--Device-systemDateTime-function setTimezone(timezone: string, callback: AsyncCallback<void>): void--><!--Device-systemDateTime-function setTimezone(timezone: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timezone | string | 是 | 系统时区。 具体可见 支持的系统时区 。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes: 1. The operation is restricted by the OS-account constraint. 2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setTimezone('Asia/Shanghai', (error: BusinessError) => {
    if (error) {
      console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`Succeeded in setting timezone.`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemDateTime.setTimezone('Asia/Jakarta', (error: BusinessError | null) => {
    if (error) {
      console.error(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.error(`Succeeded in setting timezone.`);
  });
} catch(error: BusinessError) {
  console.error(`setTimezone error: ${error.message}, code: ${error.code}`);
}
```


## setTimezone

```TypeScript
function setTimezone(timezone: string): Promise<void>
```

设置系统时区，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TIME_ZONE

<!--Device-systemDateTime-function setTimezone(timezone: string): Promise<void>--><!--Device-systemDateTime-function setTimezone(timezone: string): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timezone | string | 是 | 系统时区。具体可见 支持的系统时区 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes: 1. The operation is restricted by the OS-account constraint. 2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setTimezone('Asia/Shanghai').then(() => {
    console.info(`Succeeded in setting timezone.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set timezone. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  await systemDateTime.setTimezone('Europe/Moscow');
  systemDateTime.getTimezone((error: BusinessError | null, data: string | undefined) => {
    if (error) {
      console.error(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.error(`Succeeded in getting timezone : ${data}`);
  });
} catch(error: BusinessError) {
  console.error(`setTimezone error: ${error.message}, code: ${error.code}`);
}
```

