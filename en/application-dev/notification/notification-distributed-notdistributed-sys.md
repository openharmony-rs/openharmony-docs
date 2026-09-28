# Cross-Device Notification Management (for System Applications Only)

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b0e965054b682272b6c9e3890a6020b1129a6551 translatedAt=2026-08-22T02:17:15.332Z pushedAt=2026-08-22T07:06:12.650Z -->

By default, notification messages are subject to [cross-device collaboration](notification-glossary.md#cross-device-collaboration). If an application has implemented cross-device collaboration through the distributed communication capability (for example, SMS notification messages are synchronized by the SMS application itself to devices such as wearables, tablets, and PCs/2-in-1 devices), the collaborative devices of [distributed notification](notification-glossary.md#distributed-notification) must be managed to prevent notification messages from being repeatedly sent on different devices.

Since API version 18, a system application is supported to publish notifications in the following manners:

- If a notification of an application is published only on the current device, set the **notDistributed** field in the [NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest-sys.md) parameter to **true**.

- If a notification of an application is published based on the device management list, set the **notDistributed** field in the [NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest-sys.md) parameter to **false** and **forceDistributed** to **true**.

## Available APIs

| **API** | **Description**| **Notes**|
| -------- | -------- |-------- |
| [publish](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerpublish)(request: NotificationRequest, callback: AsyncCallback\<void\>): void | Publishes a notification.| For details, see the description of the **notDistributed** and **forceDistributed** fields in the [NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest-sys.md) object.|

## Prerequisites

 - The user has connected the watch to the phone through the Huawei Health app.

 - The user has turned on the switch for syncing notifications from phone to watch for specified applications in **Huawei Health** > **Devices** > **Notifications** on their phones.

## How to Develop

1. Import the related modules.

    ```typescript
    import { notificationManager } from '@kit.NotificationKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    ```

2. Manage the [cross-device collaboration](notification-glossary.md#cross-device-collaboration) of notification messages.

  - Publish the notification only on the current device.

    ```typescript
    // publish callback
    let publishCallback = (err: BusinessError): void => {
      if (err) {
        console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
      } else {
        console.info(`Succeeded in publishing notification.`);
      }
    }
    // NotificationRequest object
    let notificationRequest: notificationManager.NotificationRequest = {
      id: 1,
      content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
          title: 'test_title',
          text: 'test_text',
          additionalText: 'test_additionalText'
        }
      },
      // Set the notification to be published only on the current device.
      notDistributed: true
    };
    notificationManager.publish(notificationRequest, publishCallback);
    ```

  - Publish the notification across devices based on the device management list.

    ```typescript
    // publish callback
    let publishCallback = (err: BusinessError): void => {
      if (err) {
        console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
      } else {
        console.info(`Succeeded in publishing notification.`);
      }
    }
    // NotificationRequest object
    let notificationRequest: notificationManager.NotificationRequest = {
      id: 1,
      content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
          title: 'test_title',
          text: 'test_text',
          additionalText: 'test_additionalText'
        }
      },
      // forceDistributed takes effect only when the application is in the device management list and the notDistributed field is set to false. If forceDistributed is set to false, the notification is published to the devices according to the device management list.
      notDistributed: false,
      forceDistributed: false
    };
    notificationManager.publish(notificationRequest, publishCallback);
    ```