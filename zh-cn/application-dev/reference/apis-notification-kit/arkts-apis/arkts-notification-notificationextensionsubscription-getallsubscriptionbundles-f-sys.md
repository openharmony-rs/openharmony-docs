# getAllSubscriptionBundles（系统接口）

## getAllSubscriptionBundles

```TypeScript
function getAllSubscriptionBundles(): Promise<BundleOption[]>
```

获取所有具有ohos.permission.SUBSCRIBE\_NOTIFICATION权限并且实现了 [NotificationSubscriberExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的应用列表。 使用Promise异步回调。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationExtensionSubscription-function getAllSubscriptionBundles(): Promise<BundleOption[]>--><!--Device-notificationExtensionSubscription-function getAllSubscriptionBundles(): Promise<BundleOption[]>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleOption[]&gt; | Promise对象，返回所有具有 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
notificationExtensionSubscription.getAllSubscriptionBundles().then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
notificationExtensionSubscription.getAllSubscriptionBundles().then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`getAllSubscriptionBundles fail, code is ${error.code}, message is ${error.message}`);
});
```

