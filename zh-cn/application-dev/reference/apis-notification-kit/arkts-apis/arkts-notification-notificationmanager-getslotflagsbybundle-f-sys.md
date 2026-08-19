# getSlotFlagsByBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getSlotFlagsByBundle

```TypeScript
function getSlotFlagsByBundle(bundle: BundleOption): Promise<long>
```

获取指定应用的通知渠道标识位。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getSlotFlagsByBundle(bundle: BundleOption): Promise<long>--><!--Device-notificationManager-function getSlotFlagsByBundle(bundle: BundleOption): Promise<long>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | 以Promise形式返回获取指定应用的通知渠道标识位。 <br>- bit0：铃声提示。0表示关闭，1表示开启。 <br>- bit1：锁屏。0表示关闭，1表示开启。 <br>- bit2：横幅。0表示关闭，1表示开启。 <br>- bit3：亮屏。0表示关闭，1表示开启。 <br>- bit4：振动。0表示关闭，1表示开启。 <br>- bit5：状态栏通知图标。0表示关闭，1表示开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle: notificationManager.BundleOption = {
    bundle: 'bundleName1',
};
notificationManager.getSlotFlagsByBundle(bundle).then((data : number) => {
    console.info(`getSlotFlagsByBundle success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSlotFlagsByBundle failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle: notificationManager.BundleOption = {
    // 需根据实际情况进行替换
    bundle: 'bundleName1',
};
notificationManager.getSlotFlagsByBundle(bundle).then((data: long) => {
    console.info(`getSlotFlagsByBundle success, data: ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
    let error: BusinessError = err as BusinessError;
    console.error(`getSlotFlagsByBundle failed, code is ${error.code}, message is ${error.message}`);
});
```

