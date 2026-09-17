# publish

## Modules to Import

```TypeScript
```

## publish

```TypeScript
function publish(event: string, callback: AsyncCallback<void>): void
```

Publishes a common event with given properties. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [publish](arkts-basicservices-commoneventmanager-publish-f.md)(event: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result of publishing a common event. |

**Examples**

```TypeScript
import Base from '@ohos.base';

// Callback for common event publication.
let publishCallBack = (err: Base.BusinessError) => {
    if (err.code) {
        console.error(`publish failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info('publish');
    }
}

// Publish a common event.
commonEvent.publish("event", publishCallBack);
```

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

// Information of a common event.
let options:CommonEventManager.CommonEventPublishData = {
    code: 0,             // Initial code of the common event.
    data: "initial data", // Initial data of the common event.
    isOrdered: true  // The common event is an ordered one.
};

// Callback for common event publication.
let publishCallBack = (err: Base.BusinessError) => {
    if (err.code) {
        console.error(`publish failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("publish");
    }
}

// Publish a common event.
commonEvent.publish("event", options, publishCallBack);
```


## publish

```TypeScript
function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback<void>): void
```

Publishes a common event with given properties. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [publish](arkts-basicservices-commoneventmanager-publish-f.md)(event: string, options: CommonEventPublishData, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| options | [CommonEventPublishData](arkts-basicservices-commoneventpublishdata-commoneventpublishdata-i.md) | Yes | Properties of the common event to publish. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result of publishing a common event. |

**Examples**

See [publish](#publish)
