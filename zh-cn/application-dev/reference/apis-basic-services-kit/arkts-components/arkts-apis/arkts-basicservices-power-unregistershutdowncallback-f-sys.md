# unregisterShutdownCallback（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## unregisterShutdownCallback

```TypeScript
function unregisterShutdownCallback(callback?: Callback<void>): void
```

取消订阅电源关机或重启的回调提醒。使用callback同步回调。此方法与power.registerShutdownCallback配对使用，必须在先调用registerShutdownCallback订阅回调后，再调用此方法取消订阅。

**起始版本：** 23

**需要权限：** ohos.permission.REBOOT

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数，无返回值。取消订阅成功后会调用该回调函数。不传入此参数时，取消订阅仍生效，但不会触发回调通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
try {
    power.unregisterShutdownCallback(() => {
        console.info('unsubscribe shutdown success.');
    });
    console.info('unregister shutdown callback success.');
} catch (err) {
    console.error(`Failed to unregister shutdown callback. Code: ${err.code}, message: ${err.message}`);
}
```
