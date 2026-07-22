# registerShutdownCallback（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## registerShutdownCallback

```TypeScript
function registerShutdownCallback(callback: Callback<boolean>): void
```

订阅电源关机或重启的回调提醒。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.REBOOT

<!--Device-power-function registerShutdownCallback(callback: Callback<boolean>): void--><!--Device-power-function registerShutdownCallback(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回true表示重启；返回false表示关机。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try {
    power.registerShutdownCallback((isReboot: boolean) => {
        console.info('device is reboot: ' + isReboot);
    });
    console.info('register shutdown callback success.');
} catch (err) {
    console.error(`Failed to register shutdown callback. Code: ${err.code}, message: ${err.message}`);
}

```

