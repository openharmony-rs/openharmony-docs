# disableUserGrantedByBundle

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## disableUserGrantedByBundle

```TypeScript
function disableUserGrantedByBundle(bundle: GrantedBundleInfo): Promise<void>
```

关闭本应用中“已获取的本机通知”列表中指定应用的开关状态。使用promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.SUBSCRIBE_NOTIFICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationExtensionSubscription-function disableUserGrantedByBundle(bundle: GrantedBundleInfo): Promise<void>--><!--Device-notificationExtensionSubscription-function disableUserGrantedByBundle(bundle: GrantedBundleInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md) | 是 | 应用的包信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.Database operation failed. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-无效的包信息) | The specified bundle is invaild. |

**示例**

```TypeScript
let bundle: notificationExtensionSubscription.GrantedBundleInfo = {
  bundleName: 'com.example.myapplication',
  appIndex: 0
};
notificationExtensionSubscription.disableUserGrantedByBundle(bundle).then(() => {
  console.info(`disableUserGrantedByBundle successfully`);
}).catch((err: BusinessError) => {
  console.error(`disableUserGrantedByBundle fail, code is ${err.code}, message is ${err.message}`);
});
```
