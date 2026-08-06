# getUserGrantedEnabledBundles

## getUserGrantedEnabledBundles

```TypeScript
function getUserGrantedEnabledBundles(): Promise<GrantedBundleInfo[]>
```

获取本应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.SUBSCRIBE_NOTIFICATION

<!--Device-notificationExtensionSubscription-function getUserGrantedEnabledBundles(): Promise<GrantedBundleInfo[]>--><!--Device-notificationExtensionSubscription-function getUserGrantedEnabledBundles(): Promise<GrantedBundleInfo[]>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GrantedBundleInfo[]&gt; | Promise对象，返回本应用中“已获取的本机通知”通知开关开启的应用列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
notificationExtensionSubscription.getUserGrantedEnabledBundles().then((data: notificationExtensionSubscription.GrantedBundleInfo[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
notificationExtensionSubscription.getUserGrantedEnabledBundles().then((data: notificationExtensionSubscription.GrantedBundleInfo[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((error: Error) => {
  let err = error as BusinessError
  console.error(`getUserGrantedEnabledBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

