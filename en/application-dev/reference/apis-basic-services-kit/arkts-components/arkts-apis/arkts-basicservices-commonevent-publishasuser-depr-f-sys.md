# publishAsUser (System API)

## Modules to Import

```TypeScript
```

## publishAsUser

```TypeScript
function publishAsUser(event: string, userId: number, callback: AsyncCallback<void>): void
```

Publishes a common event to a specific user. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [publishAsUser](arkts-basicservices-commoneventmanager-publishasuser-f-sys.md)(event: string, userId: number, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| userId | number | Yes | ID of the user to whom the common event is published. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the common event publication result. |

**Examples**

```TypeScript
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


<a id="publishasuser-1"></a>

## publishAsUser

```TypeScript
function publishAsUser(
    event: string,
    userId: number,
    options: CommonEventPublishData,
    callback: AsyncCallback<void>
  ): void
```

Publishes a common event with given properties to a specific user. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [publishAsUser](arkts-basicservices-commoneventmanager-publishasuser-f-sys.md)( event: string, userId: number, options: CommonEventPublishData, callback: AsyncCallback&lt;void&gt; )

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| userId | number | Yes | ID of the user to whom the common event is published. |
| options | [CommonEventPublishData](arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md) | Yes | Properties of the common event to publish. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the common event publication result. |

**Examples**

```TypeScript
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
