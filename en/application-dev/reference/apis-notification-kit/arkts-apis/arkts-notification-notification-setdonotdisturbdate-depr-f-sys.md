# setDoNotDisturbDate (System API)

## Modules to Import

```TypeScript
```

## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void
```

Sets the DND time. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-1)(date: DoNotDisturbDate, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | Yes | DND time. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let setDoNotDisturbDateCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("setDoNotDisturbDate failed " + JSON.stringify(err));
  } else {
    console.info("setDoNotDisturbDate success");
  }
}

let doNotDisturbDate: Notification.DoNotDisturbDate = {
  type: Notification.DoNotDisturbType.TYPE_ONCE,
  begin: new Date(),
  end: new Date(2021, 11, 15, 18, 0)
};

Notification.setDoNotDisturbDate(doNotDisturbDate, setDoNotDisturbDateCallback);
```

<!--DelEnd-->


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>
```

Sets the DND time. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md#setdonotdisturbdate-2)(date: DoNotDisturbDate)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | Yes | DND time. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let doNotDisturbDate: Notification.DoNotDisturbDate = {
    type: Notification.DoNotDisturbType.TYPE_ONCE,
    begin: new Date(),
    end: new Date(2021, 11, 15, 18, 0)
};
Notification.setDoNotDisturbDate(doNotDisturbDate).then(() => {
  console.info("setDoNotDisturbDate success");
}).catch((err: Base.BusinessError) => {
  console.error(`setDoNotDisturbDate failed, code is ${err}`);
});
```

<!--DelEnd-->


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number, callback: AsyncCallback<void>): void
```

Sets the DND time for a specified user. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md)(date: DoNotDisturbDate, userId: number, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number, callback: AsyncCallback<void>): void--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | Yes | DND time. |
| userId | number | Yes | ID of the user for whom you want to set the DND time. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let setDoNotDisturbDateCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("setDoNotDisturbDate failed " + JSON.stringify(err));
  } else {
    console.info("setDoNotDisturbDate success");
  }
}

let doNotDisturbDate: Notification.DoNotDisturbDate = {
  type: Notification.DoNotDisturbType.TYPE_ONCE,
  begin: new Date(),
  end: new Date(2021, 11, 15, 18, 0)
};

let userId: number = 1;
Notification.setDoNotDisturbDate(doNotDisturbDate, userId, setDoNotDisturbDateCallback);
```

<!--DelEnd-->


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>
```

Sets the DND time for a specified user. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDoNotDisturbDate](arkts-notification-notificationmanager-setdonotdisturbdate-f-sys.md)(date: DoNotDisturbDate, userId: number)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | Yes | DND time. |
| userId | number | Yes | ID of the user for whom you want to set the DND time. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let doNotDisturbDate: Notification.DoNotDisturbDate = {
  type: Notification.DoNotDisturbType.TYPE_ONCE,
  begin: new Date(),
  end: new Date(2021, 11, 15, 18, 0)
};

let userId: number = 1;

Notification.setDoNotDisturbDate(doNotDisturbDate, userId).then(() => {
  console.info("setDoNotDisturbDate success");
}).catch((err: Base.BusinessError) => {
  console.error(`setDoNotDisturbDate failed, code is ${err}`);
});
```

<!--DelEnd-->
