# supportDoNotDisturbMode（系统接口）

## 导入模块

```TypeScript
```

## supportDoNotDisturbMode

```TypeScript
function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void
```

查询是否支持免打扰功能（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 查询是否支持免打扰功能回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let supportDoNotDisturbModeCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("supportDoNotDisturbMode failed " + JSON.stringify(err));
  } else {
    console.info("supportDoNotDisturbMode success");
  }
}

Notification.supportDoNotDisturbMode(supportDoNotDisturbModeCallback);
```


## supportDoNotDisturbMode

```TypeScript
function supportDoNotDisturbMode(): Promise<boolean>
```

查询是否支持免打扰功能（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回获取是否支持免打扰功能的结果。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.supportDoNotDisturbMode().then((data: boolean) => {
  console.info("supportDoNotDisturbMode success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`supportDoNotDisturbMode failed, code is ${err}`);
});
```
