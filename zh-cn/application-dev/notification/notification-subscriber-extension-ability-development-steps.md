# 通知订阅拓展能力开发步骤
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## 开发步骤

开发者在实现[NotificationSubscriberExtensionAbility](../reference/apis-ability-kit/js-apis-application-NotificationSubscriberExtensionAbility.md)提供方时，需在[DevEco Studio](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)工程中新建一个NotificationSubscriberExtensionAbility。具体步骤如下。

1. 连接穿戴设备，使用[蓝牙模块](../connectivity/connectivity-kit-intro.md#蓝牙简介)接口获取地址，然后通过subscribe/unsubscribe接口订阅或取消订阅通知。

2. 调用OpenSubscriptionSettings接口，打开通知扩展订阅设置页面，该页面以半模态弹窗显示。用户可设置通知的启用状态及模式。

3. 在entry/src/main/ets/创建目录notificationsubscriberextability。

4. 在entry/src/main/ets/notificationsubscriberextability创建NotificationSubscriberExtAbility.ets配置内容如下。
    ```ts
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import NotificationSubscriberExtensionAbility from '@ohos.application.NotificationSubscriberExtensionAbility'
    import extensionSubscription from '@ohos.notificationExtensionSubscription';

    const DOMAIN = 0x0000;
    const TAG = 'NotificationSubscriberExtAbility';

    export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
      onDestroy(): void {
        hilog.info(DOMAIN, 'testTag', `${TAG} onDestroy`);
      }

      onReceiveMessage(notificationInfo: extensionSubscription.NotificationInfo): void {
        hilog.info(DOMAIN, 'testTag', `${TAG} onReceiveMessage. notificationInfo: ${JSON.stringify(notificationInfo)}`);
      }

      onCancelMessages(hashCodes: Array<string>): void {
        hilog.info(DOMAIN, 'testTag', `${TAG} onCancelMessages. hashCodes: ${JSON.stringify(hashCodes)}`);
      }
    }
    ```
5. 在应用的module.json5文件中配置extensionAbilities。
```ts
  {
    "name": "NotificationSubscriberExtAbility",
    "srcEntry": "./ets/notificationsubscriberextability/NotificationSubscriberExtAbility.ets",
    "type": "notificationSubscriber",
    "description": "$string:NotificationSubscriberExtAbility_desc",
    "icon": "$media:layered_image",
    "label": "$string:NotificationSubscriberExtAbility_label",
    "exported": true
  }
```
## 蓝牙连接示例

1. 用户收到消息后,假如蓝牙连接是无效的,则建立蓝牙连接
2. 假如蓝牙连接已经存在,则直接使用这个连接发送消息
3. 如果使用该连接发送消息失败,则重新建立连接,如果连接能建立成功则发送消息
```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import { notificationExtensionSubscription, NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
import SppClientManager from '../utils/SppClientManager'

const DOMAIN = 0x0000;

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  sppClientManager: SppClientManager | undefined;
  onDestroy(): void {
    hilog.info(DOMAIN, 'testTag', 'onDestroy');
    this.sppClientManager!.stopConnect();
  }

  onReceiveMessage(notificationInfo: notificationExtensionSubscription.NotificationInfo): void {
    hilog.info(DOMAIN, 'testTag', `on receive message ${JSON.stringify(notificationInfo)}`)
    notificationExtensionSubscription.getSubscribeInfo()
      .then(info => {
        if (this.sppClientManager == undefined) {
          this.sppClientManager = new SppClientManager(info[0].addr);
        }
        if(this.sppClientManager.isConnect()) {
          this.sendPublishWithRetry(notificationInfo);
        } else {
          this.sppClientManager.startConnect()
          setTimeout(() => {
            this.sendPublishWithRetry(notificationInfo);
          }, 3000)
        }
      })
  }

  private sendPublishWithRetry(notificationInfo: notificationExtensionSubscription.NotificationInfo) {
    try {
      this.sppClientManager!.sendNotificationData(notificationInfo);
    } catch (err) {
      console.log(`send failed, errCode ${err.code}, errorMessage ${err.message}, and retry one times`);
      this.sppClientManager!.startConnect();
      setTimeout(() => {
        this.sppClientManager!.sendNotificationData(notificationInfo);
      }, 3000);
    }
  }

  onCancelMessages(hashCodes: Array<string>): void {
    hilog.info(DOMAIN, 'testTag', `on cancel message ${JSON.stringify(hashCodes)}`)
    notificationExtensionSubscription.getSubscribeInfo()
      .then(info => {
        if (this.sppClientManager == undefined) {
          this.sppClientManager = new SppClientManager(info[0].addr);
        }
        if(this.sppClientManager.isConnect()) {
          this.sendCancelWithRetry(hashCodes);
        } else {
          this.sppClientManager.startConnect()
          setTimeout(() => {
            this.sendCancelWithRetry(hashCodes);
          }, 3000)
        }
      })
  }


  private sendCancelWithRetry(hashCodes: string[]) {
    this.sppClientManager!.sendCancelNotificationData(hashCodes);
    try {
      this.sppClientManager!.sendCancelNotificationData(hashCodes);
    } catch (err) {
      console.log(`send failed, errCode ${err.code}, errorMessage ${err.message}, and retry one times`);
      this.sppClientManager!.startConnect();
      setTimeout(() => {
        this.sppClientManager!.sendCancelNotificationData(hashCodes);
      }, 3000);
    }
  }
}
```
<!--@[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/ThirdpartyWerableDemo/entry/src/main/ets/extensionability/NotificationSubscriberExtAbility.ets)-->
注意：请勿频繁建立链接，可能会影响功能。