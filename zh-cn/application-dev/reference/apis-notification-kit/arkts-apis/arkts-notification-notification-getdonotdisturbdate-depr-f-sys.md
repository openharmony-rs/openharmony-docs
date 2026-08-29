# getDoNotDisturbDate（系统接口）

## 导入模块

```TypeScript
```

## getDoNotDisturbDate

```TypeScript
function getDoNotDisturbDate(callback: AsyncCallback<DoNotDisturbDate>): void
```

查询免打扰时间（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DoNotDisturbDate&gt; | 是 | 查询免打扰时间回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let getDoNotDisturbDateCallback = (err: Base.BusinessError, data: Notification.DoNotDisturbDate) => {
  if (err) {
    console.error("getDoNotDisturbDate failed " + JSON.stringify(err));
  } else {
    console.info("getDoNotDisturbDate success");
  }
}

Notification.getDoNotDisturbDate(getDoNotDisturbDateCallback);
```


## getDoNotDisturbDate

```TypeScript
function getDoNotDisturbDate(): Promise<DoNotDisturbDate>
```

查询免打扰时间（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;DoNotDisturbDate&gt; | 以Promise形式返回查询到的免打扰时间。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.getDoNotDisturbDate().then((data: Notification.DoNotDisturbDate) => {
  console.info("getDoNotDisturbDate success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`getDoNotDisturbDate failed, code is ${err}`);
});
```


## getDoNotDisturbDate

```TypeScript
function getDoNotDisturbDate(userId: number, callback: AsyncCallback<DoNotDisturbDate>): void
```

查询指定用户的免打扰时间（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DoNotDisturbDate&gt; | 是 | 查询免打扰时间回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let getDoNotDisturbDateCallback = (err: Base.BusinessError, data: Notification.DoNotDisturbDate) => {
  if (err) {
    console.error("getDoNotDisturbDate failed " + JSON.stringify(err));
  } else {
    console.info("getDoNotDisturbDate success");
  }
}

let userId: number = 1;

Notification.getDoNotDisturbDate(userId, getDoNotDisturbDateCallback);
```


## getDoNotDisturbDate

```TypeScript
function getDoNotDisturbDate(userId: number): Promise<DoNotDisturbDate>
```

查询指定用户的免打扰时间（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDoNotDisturbDate](arkts-notification-notificationmanager-getdonotdisturbdate-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;DoNotDisturbDate&gt; | 以Promise形式返回查询到的免打扰时间。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let userId: number = 1;

Notification.getDoNotDisturbDate(userId).then((data: Notification.DoNotDisturbDate) => {
  console.info("getDoNotDisturbDate success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`getDoNotDisturbDate failed, code is ${err}`);
});
```
