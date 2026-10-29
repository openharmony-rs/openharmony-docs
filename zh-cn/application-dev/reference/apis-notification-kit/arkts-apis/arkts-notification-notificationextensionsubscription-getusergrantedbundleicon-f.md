# getUserGrantedBundleIcon

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## getUserGrantedBundleIcon

```TypeScript
function getUserGrantedBundleIcon(bundleName: string): Promise<image.PixelMap>
```

查询本应用中“已获取的本机通知”列表中开关状态为开的应用图标。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.SUBSCRIBE_NOTIFICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationExtensionSubscription-function getUserGrantedBundleIcon(bundleName: string): Promise<image.PixelMap>--><!--Device-notificationExtensionSubscription-function getUserGrantedBundleIcon(bundleName: string): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise对象，返回应用图标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.Failed to obtain or decode the application icon. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-无效的包信息) | The specified bundle is invaild. Possible cause: 1.The application is not in the list. 2.The application is disabled. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';

notificationExtensionSubscription.getUserGrantedBundleIcon('com.example.myapplication').then((data: image.PixelMap) => {
  console.info(`getUserGrantedBundleIcon successfully, pixel bytes number is ${data.getPixelBytesNumber()}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedBundleIcon fail, code is ${err.code}, message is ${err.message}`);
});
```
