# setAutoTimeStatus（系统接口）

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

<a id="setautotimestatus"></a>
## setAutoTimeStatus

```TypeScript
function setAutoTimeStatus(status: boolean): Promise<void>
```

设置自动设置时间开关状态，使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.SET_TIME

<!--Device-systemDateTime-function setAutoTimeStatus(status: boolean): Promise<void>--><!--Device-systemDateTime-function setAutoTimeStatus(status: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Time

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | boolean | 是 | 设置自动设置时间开关状态。<br/>- true：表示打开自动设置时间开关。 <br/>- false：表示关闭自动设置时间开关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [13000001](../../apis-basic-services-kit/errorcode-time.md#13000001-网络或操作系统异常) | Network connection error or OS error. Possible causes:1. System memory is insufficient;2. Calls the underlying system interface failed. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.setAutoTimeStatus(true).then(() => {
    console.info(`Succeeded in setting autotime.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to set autotime. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to set autotime. Code: ${error.code}, message: ${error.message}`);
}

```

