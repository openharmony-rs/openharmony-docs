# setAutoTimeStatus（系统接口）

## setAutoTimeStatus

```TypeScript
function setAutoTimeStatus(status: boolean): Promise<void>
```

设置自动设置时间开关状态，使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.SET_TIME

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | boolean | 是 | 设置自动设置时间开关状态。<br/>- true：表示打开自动设置时间开关。<br/>- false：表示关闭自动设置时间开关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [13000001](../../errorcode-universal.md#13000001-Network) | Network connection error or OS error. Possible causes:<br/>1. System memory is insufficient;<br/>2. Calls the underlying system interface failed. |
| [204](../../errorcode-universal.md#204-Access) | Access denied due to user access control policy. Possible causes:<br/>1. The operation is restricted by the OS-account constraint.<br/>2. The required privilege for the operation has not been granted.&lt;br&gt;**适用版本：** 24+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setAutoTimeStatus(true).then(() => {
    console.info(`Succeeded in setting autotime.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to set autotime. message: ${error.message}, code: ${error.code}`);
}

```

