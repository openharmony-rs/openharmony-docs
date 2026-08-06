# getUserGrantedState（系统接口）

## getUserGrantedState

```TypeScript
function getUserGrantedState(targetBundle: BundleOption): Promise<boolean>
```

查询指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationExtensionSubscription-function getUserGrantedState(targetBundle: BundleOption): Promise<boolean>--><!--Device-notificationExtensionSubscription-function getUserGrantedState(targetBundle: BundleOption): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetBundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 需要查询的目标应用信息。应用需要具有ohos.permission.SUBSCRIBE\_\_\_ESCAPED\_UNDERSCORE\_\_\_NOTIFICATION权限，并且实现[NotificationSubscriberExtensionAbility]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，否则返回1600022错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示目标应用的“允许获取本机通知”状态已启用； |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-无效的包信息) | The specified bundle is invalid. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedState(targetBundle).then((isOpen: boolean) => {
  if (isOpen) {
    console.info('GrantedState true');
  } else {
    console.info('GrantedState false');
  }
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedState fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // 应改为开发者需要查询的目标应用信息
    bundle: 'com.example.testnotification',
  };
notificationExtensionSubscription.getUserGrantedState(targetBundle).then((isOpen: boolean) => {
  if (isOpen) {
    console.info('GrantedState true');
  } else {
    console.info('GrantedState false');
  }
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`getUserGrantedState fail, code is ${error.code}, message is ${error.message}`);
});
```

