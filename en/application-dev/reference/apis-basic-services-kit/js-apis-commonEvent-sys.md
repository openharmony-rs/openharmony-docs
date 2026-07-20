# @ohos.commonEvent (Common Event) (System API) (Deprecated)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

This module provides APIs to publish, subscribe to, and unsubscribe from common events, as well as obtain and modify the common event result code and result data. It is applicable to scenarios where system services or apps communicate with each other through common events. This module helps you publish and subscribe to events across apps, improving collaboration efficiency between apps.

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [@ohos.commonEventManager](js-apis-commonEventManager.md) instead.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [CommonEvent](./js-apis-commonEvent.md).

## Modules to Import

```ts
import commonEvent from '@ohos.commonEvent';
```

## Support

System common events refer to events released by system services or system apps. Subscribing to these events requires specific permissions. To publish or subscribe to this type of event, you must follow the event-specific definitions.

For details about the definitions of all system common events, see [System Common Events](./common_event/commonEvent-definitions.md).

## commonEvent.publishAsUser<sup>(deprecated)</sup>

publishAsUser(event: string, userId: number, callback: AsyncCallback\<void>): void

Publishes a common event to a specific user. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [commonEventManager.publishAsUser](js-apis-commonEventManager-sys.md#commoneventmanagerpublishasuser) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**Parameters**

| Name    | Type                | Mandatory| Description                              |
| -------- | -------------------- | ---- | ---------------------------------- |
| event    | string               | Yes  | Name of the common event to publish.            |
| userId   | number               | Yes  | ID of the user to whom the common event is published.|
| callback | AsyncCallback\<void> | Yes  | Callback used to return the common event publication result.            |

**Example**

```ts
import Base from '@ohos.base';

// Callback for common event publication
let publishCallBack = (err:Base.BusinessError) => {
    if (err.code) {
        console.error(`Failed to publishAsUser. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('publishAsUser');
    }
}

// Specify the user to whom the common event will be published.
const userId = 100;

// Publish a common event.
commonEvent.publishAsUser('event', userId, publishCallBack);
```

## commonEvent.publishAsUser<sup>(deprecated)</sup>

publishAsUser(event: string, userId: number, options: CommonEventPublishData, callback: AsyncCallback\<void>): void

Publishes a common event with given properties to a specific user. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [commonEventManager.publishAsUser](js-apis-commonEventManager-sys.md#commoneventmanagerpublishasuser-1) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**Parameters**

| Name    | Type                  | Mandatory| Description                  |
| -------- | ---------------------- | ---- | ---------------------- |
| event    | string                 | Yes  | Name of the common event to publish. |
| userId   | number | Yes| ID of the user to whom the common event is published.|
| options  | [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) | Yes  | Properties of the common event to publish.|
| callback | AsyncCallback\<void>   | Yes  | Callback used to return the common event publication result. |

**Example**


```ts
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

// Information of a common event.
let options:CommonEventManager.CommonEventPublishData = {
    code: 0,              // Initial code of the common event.
    data: 'initial data', // Initial data of the common event.
};

// Callback for common event publication
let publishCallBack = (err:Base.BusinessError) => {
    if (err.code) {
        console.error(`Failed to publishAsUser. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('publishAsUser');
    }
}

// Specify the user to whom the common event will be published.
let userId = 100;

// Publish a common event.
commonEvent.publishAsUser('event', userId, options, publishCallBack);
```
