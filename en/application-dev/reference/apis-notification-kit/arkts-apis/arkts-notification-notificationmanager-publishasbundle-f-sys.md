# publishAsBundle (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## publishAsBundle

```TypeScript
function publishAsBundle(
    request: NotificationRequest,
    representativeBundle: string,
    userId: number,
    callback: AsyncCallback<void>
  ): void
```

Publishes a notification through the reminder agent. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Yes | Content and related configuration of the notification to publish. |
| representativeBundle | string | Yes | Bundle name of the application whose notification function is taken over by the reminder agent. |
| userId | number | Yes | User ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The device does not support geofencing.<br>**Applicable version:** 23 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-notification-slot-disabled) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |
| [1600009](../errorcode-notification.md#1600009-notification-sending-limit-reached) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-no-related-permission) | The right of liveView is not enabled.<br>**Applicable version:** 26.0.0 and later |
| [1600015](../errorcode-notification.md#1600015-duplicate-configurations-not-allowed-for-the-current-notification-status) | The current notification status does not support duplicate configurations. |
| [1600016](../errorcode-notification.md#1600016-updated-notification-version-outdated) | The notification version for this update is too low. |
| [1600020](../errorcode-notification.md#1600020-applications-in-the-permission-control-list-are-not-allowed-to-publish-notifications) | The application is not allowed to send notifications due to permission settings. |
| [1600025](../errorcode-notification.md#1600025-geofencing-disabled) | Geofencing disabled.<br>**Applicable version:** 23 and later |
| [1600026](../errorcode-notification.md#1600026-location-disabled) | The location switch is off.<br>**Applicable version:** 23 and later |
| [1600027](../errorcode-notification.md#1600027-awareness-suggestions-switch-of-the-location-service-disabled) | The "Awareness & suggestions" switch of the location-based service is off.<br>**Applicable version:** 23 and later |
| [1600029](../errorcode-notification.md#1600029-failed-to-find-the-extensionability-for-the-custom-extension-area-of-the-live-view-widget) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**Applicable version:** 26.0.0 and later |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-failed-to-connect-to-the-server) | Network unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// publishAsBundle callback
let callback = (err: BusinessError): void => {
    if (err) {
        console.error(`publishAsBundle failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("publishAsBundle success");
    }
}
// Bundle name of the application whose notification function is taken over by the reminder agent
let representativeBundle: string = "com.example.demo";
// Use the actual user ID when calling the API.
let userId: number = 100;
// NotificationRequest object
let request: notificationManager.NotificationRequest = {
    id: 1,
    content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
            title: "test_title",
            text: "test_text",
            additionalText: "test_additionalText"
        }
    }
};
notificationManager.publishAsBundle(request, representativeBundle, userId, callback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Bundle name of the application whose notification function is taken over by the reminder agent
let representativeBundle: string = "com.example.demo";
// Use the actual user ID when calling the API.
let userId: number = 100;
// NotificationRequest object
let request: notificationManager.NotificationRequest = {
    id: 1,
    content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
            title: "test_title",
            text: "test_text",
            additionalText: "test_additionalText"
        }
    }
};
notificationManager.publishAsBundle(request, representativeBundle, userId).then(() => {
    console.info("publishAsBundle success");
}).catch((err: BusinessError) => {
    console.error(`publishAsBundle failed, code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Bundle information of the application whose notification function is taken over by the reminder agent.
let representativeBundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
// NotificationRequest object
let request: notificationManager.NotificationRequest = {
    id: 1,
    content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
            title: "test_title",
            text: "test_text",
            additionalText: "test_additionalText"
        }
    }
};
notificationManager.publishAsBundle(representativeBundle, request).then(() => {
    console.info("publishAsBundle success");
}).catch((err: BusinessError) => {
    console.error(`publishAsBundle failed, code is ${err.code}, message is ${err.message}`);
});
```


## publishAsBundle

```TypeScript
function publishAsBundle(request: NotificationRequest, representativeBundle: string, userId: number): Promise<void>
```

Publishes a notification through the reminder agent. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Yes | Content and related configuration of the notification to publish. |
| representativeBundle | string | Yes | Bundle name of the application whose notification function is taken over by the reminder agent. |
| userId | number | Yes | User ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The device does not support geofencing.<br>**Applicable version:** 23 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-notification-slot-disabled) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |
| [1600009](../errorcode-notification.md#1600009-notification-sending-limit-reached) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-no-related-permission) | The right of liveView is not enabled.<br>**Applicable version:** 26.0.0 and later |
| [1600015](../errorcode-notification.md#1600015-duplicate-configurations-not-allowed-for-the-current-notification-status) | The current notification status does not support duplicate configurations. |
| [1600016](../errorcode-notification.md#1600016-updated-notification-version-outdated) | The notification version for this update is too low. |
| [1600020](../errorcode-notification.md#1600020-applications-in-the-permission-control-list-are-not-allowed-to-publish-notifications) | The application is not allowed to send notifications due to permission settings. |
| [1600025](../errorcode-notification.md#1600025-geofencing-disabled) | Geofencing disabled.<br>**Applicable version:** 23 and later |
| [1600026](../errorcode-notification.md#1600026-location-disabled) | The location switch is off.<br>**Applicable version:** 23 and later |
| [1600027](../errorcode-notification.md#1600027-awareness-suggestions-switch-of-the-location-service-disabled) | The "Awareness & suggestions" switch of the location-based service is off.<br>**Applicable version:** 23 and later |
| [1600029](../errorcode-notification.md#1600029-failed-to-find-the-extensionability-for-the-custom-extension-area-of-the-live-view-widget) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**Applicable version:** 26.0.0 and later |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-failed-to-connect-to-the-server) | Network unreachable. |

**Examples**

See [publishAsBundle](#publishasbundle)


## publishAsBundle

```TypeScript
function publishAsBundle(representativeBundle: BundleOption, request: NotificationRequest): Promise<void>
```

Publishes a notification through the reminder agent. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| representativeBundle | [BundleOption](arkts-notification-notificationmanager-bundleoption-t.md) | Yes | Bundle information of the application whose notification function is taken over by the reminder agent. |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Yes | Content and related configuration of the notification to publish. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The device does not support geofencing.<br>**Applicable version:** 23 and later |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-notification-slot-disabled) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [1600008](../errorcode-notification.md#1600008-user-not-found) | The user does not exist. |
| [1600009](../errorcode-notification.md#1600009-notification-sending-limit-reached) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-no-related-permission) | The right of liveView is not enabled.<br>**Applicable version:** 26.0.0 and later |
| [1600015](../errorcode-notification.md#1600015-duplicate-configurations-not-allowed-for-the-current-notification-status) | The current notification status does not support duplicate configurations. |
| [1600016](../errorcode-notification.md#1600016-updated-notification-version-outdated) | The notification version for this update is too low. |
| [1600020](../errorcode-notification.md#1600020-applications-in-the-permission-control-list-are-not-allowed-to-publish-notifications) | The application is not allowed to send notifications due to permission settings. |
| [1600025](../errorcode-notification.md#1600025-geofencing-disabled) | Geofencing disabled.<br>**Applicable version:** 23 and later |
| [1600026](../errorcode-notification.md#1600026-location-disabled) | The location switch is off.<br>**Applicable version:** 23 and later |
| [1600027](../errorcode-notification.md#1600027-awareness-suggestions-switch-of-the-location-service-disabled) | The "Awareness & suggestions" switch of the location-based service is off.<br>**Applicable version:** 23 and later |
| [1600029](../errorcode-notification.md#1600029-failed-to-find-the-extensionability-for-the-custom-extension-area-of-the-live-view-widget) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**Applicable version:** 26.0.0 and later |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-failed-to-connect-to-the-server) | Network unreachable. |

**Examples**

See [publishAsBundle](#publishasbundle)
