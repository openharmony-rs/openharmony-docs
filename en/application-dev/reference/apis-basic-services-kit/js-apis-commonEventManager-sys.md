# @ohos.commonEventManager (Common Event) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=227499a15769ff89e238d0afb653f1633e59b877 translatedAt=2026-07-21T08:29:08.998Z pushedAt=2026-07-22T06:40:26.298Z -->

This module provides system APIs related to common events, including publishing common events to specified users, removing sticky common events, and enabling or disabling static subscription events.

> **NOTE**
>
> - This module supports both ArkTS-Dyn and ArkTS-Sta.
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [CommonEventManager](./js-apis-commonEventManager.md).

## Modules to Import

```ts
import { commonEventManager } from '@kit.BasicServicesKit';
```

## Support

A system common event is an event that is published by a system service or system application and requires specific permissions to subscribe to. To publish or subscribe to this type of event, you must follow the event-specific definitions.

For details about the enums of all system common events, see [System Common Events (System API)](./common_event/commonEventManager-definitions-sys.md).

**System capability**: SystemCapability.Notification.CommonEvent

**ArkTS-Dyn start version:** 9

**ArkTS-Sta start version:** 23

## commonEventManager.publishAsUser

ArkTS-Dyn: publishAsUser(event: string, userId: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: publishAsUser(event: string, userId: int, callback: AsyncCallback\<void>): void

Publishes a common event to a specified user. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**ArkTS-Dyn start version:** 9

**ArkTS-Sta start version:** 23

**Parameters**

| Name    | Type                | Mandatory| Description                              |
| -------- | -------------------- | ---- | ---------------------------------- |
| event    | string               | Yes   | Name of the common event to publish. For details, see [System Common Events (System API)](./common_event/commonEventManager-definitions-sys.md).             |
| userId   | ArkTS-Dyn: number<br/>ArkTS-Sta: int               | Yes   | ID of the user who will receive the common event. |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API.                     |
| 1500003  | The common event sending frequency too high.<br> Applicable versions: 20+ |
| 1500006  | Invalid userId.<br> Applicable versions: 21+ |
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |
| 1500009  | Failed to obtain system parameters.  |

**Example**

**ArkTS-Dyn example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Specify the user to whom the common event will be published.
let userId = 100;

// Publish a common event.
try {
    commonEventManager.publishAsUser('event', userId, (err: BusinessError) => {
      if (err) {
        console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('publishAsUser');
    });
} catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

**ArkTS-Sta example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Specify the target user.
let userId = 1;

// Publish the common event.
try {
    commonEventManager.publishAsUser('event', userId, (err: BusinessError | null) => {
      if (err) {
        console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('publishAsUser');
    });
} catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

## commonEventManager.publishAsUser

ArkTS-Dyn: publishAsUser(event: string, userId: number, options: CommonEventPublishData, callback: AsyncCallback\<void>): void

ArkTS-Sta: publishAsUser(event: string, userId: int, options: CommonEventPublishData, callback: AsyncCallback\<void>): void

Publishes a common event to a specified user and specifies the information to be published. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**ArkTS-Dyn start version:** 9

**ArkTS-Sta start version:** 23

**Parameters**

| Name    | Type                  | Mandatory| Description                  |
| -------- | ---------------------- | ---- | ---------------------- |
| event    | string                 | Yes   | Name of the common event to publish. For details, see [System Common Events (System API)](./common_event/commonEventManager-definitions-sys.md).  |
| userId   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | Yes | ID of the user who will receive the common event. |
| options  | [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) | Yes  | Properties of the common event to publish.|
| callback | AsyncCallback\<void>   | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API.                     |
| 1500003  | The common event sending frequency too high.<br> Applicable versions: 20+ |
| 1500006  | Invalid userId.<br> Applicable versions: 21+ |
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |
| 1500009  | Failed to obtain system parameters.  |

**Example**

**ArkTS-Dyn example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Information of the common event.
let options: commonEventManager.CommonEventPublishData = {
  code: 0,        // Initial code of the common event.
  data: 'initial data', // Initial data of the common event.
}

// Specify the user to whom the common event will be published.
let userId = 100;
// Publish a common event.
try {
  commonEventManager.publishAsUser('event', userId, options, (err: BusinessError) => {
    if (err) {
      console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('publishAsUser');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

**ArkTS-Sta example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Information about the common event.
let options:commonEventManager.CommonEventPublishData = {
  code: 0,// Initial code of the common event.
  data: 'initial data',// Initial data of the common event.
}

// Specify the target user.
let userId = 1;
// Publish the common event.
try {
  commonEventManager.publishAsUser('event', userId, options, (err: BusinessError | null) => {
    if (err) {
      console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('publishAsUser');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

## commonEventManager.removeStickyCommonEvent<sup>10+</sup>

removeStickyCommonEvent(event: string, callback: AsyncCallback\<void>): void

Removes a sticky common event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions**: ohos.permission.COMMONEVENT_STICKY

**System API**: This is a system API.

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name  | Type                | Mandatory| Description                            |
| -------- | -------------------- | ---- | -------------------------------- |
| event    | string               | Yes   | Sticky common event to remove. For details, see [System Common Events (System API)](./common_event/commonEventManager-definitions-sys.md).       |
| callback | AsyncCallback\<void> | Yes   | Callback used to return the result. If the sticky common event is successfully removed, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 202      | Permission verification failed. A non-system application calls a system API.                     |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      |
| 1500004  | A third-party application cannot send system common events.                |
| 1500007  | Failed to send the message to the common event service.             |
| 1500008  | Failed to initialize the common event service.     |

**Example**

**ArkTS-Dyn example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.removeStickyCommonEvent('sticky_event', (err: BusinessError) => {
  if (err) {
    console.error(`removeStickyCommonEvent failed, errCode: ${err.code}, errMes: ${err.message}`);
    return;
  }
  console.info(`removeStickyCommonEvent success`);
});
```

**ArkTS-Sta example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.removeStickyCommonEvent('sticky_event', (err: BusinessError | null) => {
  if (err) {
    console.error(`removeStickyCommonEvent failed, errCode: ${err.code}, errMes: ${err.message}`);
    return;
  }
  console.info(`removeStickyCommonEvent success`);
});
```

## commonEventManager.removeStickyCommonEvent<sup>10+</sup>

removeStickyCommonEvent(event: string): Promise\<void>

Removes a sticky common event that has been published. This API uses a promise to return the result.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.COMMONEVENT_STICKY

**System API**: This is a system API.

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| event  | string | Yes   | Sticky common event to remove. For details, see [System Common Events (System API)](./common_event/commonEventManager-definitions-sys.md). |

**Return value**

| Type          | Description                        |
| -------------- | ---------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 201      | Permission verification failed. The app does not have the permission required to call the API.     |
| 202      | Permission verification failed. A non-system app calls a system API.                     |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      |
| 1500004  | A third-party application cannot send system common events.                |
| 1500007  | Failed to send the message to the common event service.             |
| 1500008  | Failed to initialize the common event service.     |

**Example**

**ArkTS-Dyn example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.removeStickyCommonEvent('sticky_event').then(() => {
  console.info(`removeStickyCommonEvent success`);
}).catch ((err: BusinessError) => {
  console.error(`removeStickyCommonEvent failed, errCode: ${err.code}, errMes: ${err.message}`);
});
```

**ArkTS-Sta example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.removeStickyCommonEvent('sticky_event').then(() => {
  console.info(`removeStickyCommonEvent success`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`removeStickyCommonEvent failed, errCode: ${error.code}, errMes: ${error.message}`);
});
```

## commonEventManager.setStaticSubscriberState<sup>10+</sup>

setStaticSubscriberState(enable: boolean, callback: AsyncCallback\<void>): void

Enables or disables static subscription for an application. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| enable  | boolean | Yes   | Whether static subscription is enabled.<br> **true**: enabled; **false**: disabled. |
| callback  | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API.                     |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      |
| 1500007  | Failed to send the message to the common event service.             |
| 1500008  | Failed to initialize the common event service.     |

**Example**

**ArkTS-Dyn example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.setStaticSubscriberState(true, (err: BusinessError) => {
  if (err.code != 0) {
    console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMes: ${err.message}`);
    return;
  }
  console.info(`setStaticSubscriberState success`);
});
```

**ArkTS-Sta example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.setStaticSubscriberState(true, (err: BusinessError | null) => {
  if (err != null) {
    console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMes: ${err.message}`);
    return;
  }
  console.info(`setStaticSubscriberState success`);
});
```

## commonEventManager.setStaticSubscriberState<sup>10+</sup>

setStaticSubscriberState(enable: boolean): Promise\<void>

Enables or disables static subscription for an application. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**ArkTS-Dyn start version:** 10

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| enable  | boolean | Yes  | Whether static subscription is enabled.<br> **true**: enabled; **false**: disabled. |

**Return value**

| Type          | Description                        |
| -------------- | ---------------------------- |
| Promise\<void> |  Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 202      | Permission verification failed. A non-system app calls a system API.                     |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      |
| 1500007  | Failed to send the message to the common event service.             |
| 1500008  | Failed to initialize the common event service.     |

**Example**

ArkTS-Dyn example:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.setStaticSubscriberState(false).then(() => {
  console.info(`setStaticSubscriberState success`);
}).catch ((err: BusinessError) => {
  console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMes: ${err.message}`);
});
```

**ArkTS-Sta example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.setStaticSubscriberState(false).then(() => {
  console.info(`setStaticSubscriberState success`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`setStaticSubscriberState failed, errCode: ${error.code}, errMes: ${error.message}`);
});
```

## commonEventManager.setStaticSubscriberState<sup>12+</sup>

setStaticSubscriberState(enable: boolean, events?: Array\<string>): Promise\<void>

Enables or disables static subscription to a common event for the current application. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**ArkTS mode:** This API is only applicable to ArkTS-Dyn.

**Related API:** The corresponding ArkTS-Sta API is [setStaticSubscriberState](#commoneventmanagersetstaticsubscriberstate).

**ArkTS-Dyn start version:** 12

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------------- | ---- | ---------------------------------------------------- |
| enable | boolean | Yes | Whether the static subscription event is enabled. **true**: enable, **false**: disable. |
| events | Array\<string> | No | Array of common event names to set. The array is empty by default, indicating that the status of all common events subscribed to in static mode by the current application is to be set. |

**Return value**

| Type | Description |
| -------------- | ------------------------------------ |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID | Error Message |
| -------- | ------------------------------------------------------ |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 1500007 | Failed to send the message to the common event service. |
| 1500008 | Failed to initialize the common event service. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let eventName: string[] = ['usual.event.SEND_DATA'];
commonEventManager.setStaticSubscriberState(true, eventName).then(() => {
  console.info(`setStaticSubscriberState success, state is ${true}`);
}).catch((err: BusinessError) => {
  console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMes: ${err.message}`);
});
```

## commonEventManager.setStaticSubscriberState

setStaticSubscriberState(enable: boolean, events: Array\<string>): Promise\<void>

Enables or disables the static subscription event for the current application and records the event name. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.CommonEvent

**System API**: This is a system API.

**ArkTS mode:** This API is only applicable to ArkTS-Sta.

**Related API:** The corresponding ArkTS-Dyn API is [setStaticSubscriberState](#commoneventmanagersetstaticsubscriberstate12).

**ArkTS-Sta start version:** 23

**Parameters**

| Name| Type         | Mandatory| Description                                                |
| ------ | ------------- | ---- | ---------------------------------------------------- |
| enable | boolean       | Yes  | Whether static subscription is enabled.<br> **true**: enabled; **false**: disabled.|
| events | Array\<string> | Yes  | Event names recorded.                                   |

**Return value**

| Type          | Description                                |
| -------------- | ------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 202      | not system app.                     |  
| 401     | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed.      | 
| 1500007  | Failed to send the message to the common event service.        |
| 1500008  | Failed to initialize the common event service. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let evenName: string[] = ['usual.event.SEND_DATA'];
commonEventManager.setStaticSubscriberState(true, evenName).then(() => {
  console.info(`setStaticSubscriberState success, state is ${true}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`setStaticSubscriberState failed, errCode: ${error.code}, errMes: ${error.message}`);
});
```