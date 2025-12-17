# 使用RunningLockType.BACKGROUND_USER_IDLE运行锁

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @w_Machine_cc-->

## 场景介绍

用户不活动一段时间后，通常系统会尝试进入自动休眠，使用RunningLockType.BACKGROUND_USER_IDLE运行锁，保证在持锁过程中系统不会进入自动休眠，保证业务正常运行。

## 环境准备

### 环境要求

- 开发工具及配置：

  DevEco Studio作为驱动开发工具，是进行驱动开发必备条件之一，开发者可以使用该工具进行开发、调试、打包等操作。请[下载安装](https://developer.huawei.com/consumer/cn/download/)该工具，并参考[DevEco Studio使用指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)中的[创建工程及运行](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-create-new-project)进行基本的操作验证，保证DevEco Studio可正常运行。


- SDK版本配置：
  RunningLockType.BACKGROUND_USER_IDLE类型的运行锁，所需SDK版本为API23及以上才可使用。


- HDC配置：

  HDC（HarmonyOS Device Connector）是为开发人员提供的用于调试的命令行工具，通过该工具可以在Windows/Linux/Mac系统上与真实设备或者模拟器进行交互，详细参考[HDC配置](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hdc)。

### 搭建环境

- 在PC上安装[DevEco Studio](https://developer.huawei.com/consumer/cn/download/deveco-studio)，要求版本在4.1及以上。
- 将public-SDK更新到API 23或以上<!--Del-->，更新SDK的具体操作可参见[更新指南](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/faqs/full-sdk-switch-guide.md)<!--DelEnd-->。
- PC安装HDC工具，通过该工具可以在Windows/Linux/Mac系统上与真实设备或者模拟器进行交互。
- 用USB线缆将搭载OpenHarmony的设备连接到PC。

## 开发指导

### 接口说明

#### 1. RunningLockType.BACKGROUND_USER_IDLE接口的使用约束和设备差异：
    
  - PC设备创建该类型的运行锁无权限管控，非PC设备创建该类型的运行锁要求是系统应用，非PC设备且非系统应用使用该类型锁**功能不生效**，开发时应考虑此约束。
  - 使用该接口的应用必须监听[进入强制睡眠的公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12)，在接收到该公共事件后1s内主动释放掉该锁；是否监听[退出强制睡眠的公共事件](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_exit_force_sleep12)并重新持有锁，由应用根据具体场景自行决策。

#### 2. 介绍自动睡眠与强制睡眠

   系统睡眠（sleep）指的是计算机系统进入一种低功耗状态，其中大部分硬件组件停止工作，只有最小必要的组件保持运行，以维持系统状态。系统睡眠分为两种主要类型：自动睡眠和强制睡眠。

   （1）自动睡眠：由系统预设的条件或用户配置自动触发的睡眠状态。通常，当计算机在一段时间内没有检测到用户活动（如键盘或鼠标输入）时，系统会自动进入睡眠状态。

   （2）强制睡眠是指用户或应用程序直接命令系统立即进入睡眠状态（如用户合上pc盖子，或主动点击菜单里的睡眠等），而不考虑当前系统状态或用户活动。

### 开发步骤

使用RunningLockType.BACKGROUND_USER_IDLE运行锁，开发示例如下：

1. 导入模块。

``` TypeScript
// 导入runningLock、commonEventManager模块
import { runningLock } from '@kit.BasicServicesKit';
import { commonEventManager } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
```

2. 创建运行锁并监听公共事件。

``` TypeScript
// RunningLockUtil.ets
type SubscriberInfo = commonEventManager.CommonEventSubscribeInfo;
type Subscriber = commonEventManager.CommonEventSubscriber;
type EventData = commonEventManager.CommonEventData;

export class CommonEventHelper {
  public static async subscribeSystemCommonEvent(info: SubscriberInfo,
    callback: (data: EventData) => void) : Promise<Subscriber | undefined> {
    try {
      if (info.events.length <= 0) {
        console.error('Subscriber event error');
        return undefined;
      }
      const subscriber: Subscriber = await commonEventManager.createSubscriber(info);
      commonEventManager.subscribe(subscriber, (error, data): void => {
        if (error) {
          console.error('Failed to callback event');
          return;
        }
        callback(data);
      });
      return subscriber;
    } catch (error) {
      console.error('Failed to subscribe system common event, err: ' + error);
      return undefined;
    }
  }

  public static async unsubscribeSystemCommonEvent(subscriber: Subscriber | undefined): Promise<boolean> {
    try {
      if (subscriber === undefined) {
        console.error('subscriber error');
        return false;
      }
      commonEventManager.unsubscribe(subscriber, (error): void => {
        if (error) {
          console.error('unsubscribe error');
        } else {
          console.info('unsubscribe success');
        }
      });
      return true;
    } catch (error) {
      console.error('Failed to unsubscribe event, err: ' + error);
      return false;
    }
  }
}

export class RunningLockUtil {
  public static recordLock: runningLock.RunningLock | undefined;

  public static holdRunningLock(): void {
    // 通过isSupport接口查询当前设备是否支持该类型锁
    if (!runningLock.isSupported(runningLock.RunningLockType.BACKGROUND_USER_IDLE)) {
        console.error('type BACKGROUND_USER_IDLE is not support in the device.');
        return;
    }
    if (RunningLockUtil.recordLock) {
      try {
        RunningLockUtil.recordLock.hold(500);
        console.info('hold running lock success');
      } catch (err) {
        console.error('hold running lock failed, err: ' + err);
      }
    } else {
      runningLock.create('running_lock_user_idle', runningLock.RunningLockType.BACKGROUND_USER_IDLE, (err: Error, lock: runningLock.RunningLock) => {
        if (typeof err === 'undefined') {
          console.info('create running lock: ' + lock);
          RunningLockUtil.recordLock = lock;
          try {
            lock.hold(500);
            console.info('hold running lock success');
          } catch (err) {
            console.error('hold running lock failed, err: ' + err);
          }
        } else {
          console.error('create running lock failed, err: ' + err);
        }
      });
    }
  }

  public static unholdRunningLock(): void {
    if (!RunningLockUtil.recordLock) {
      console.error('lock is null');
      return;
    }
    try {
      if (RunningLockUtil.recordLock.isHolding()) {
        RunningLockUtil.recordLock.unhold();
        console.info('unhold running lock success');
      }
    } catch (error) {
      console.error('unhold running lock failed, err: ' + error);
    }
  }
}
```

3. 使用运行锁。
``` TypeScript
// UserIdleTask.ets
import { CommonEventHelper, RunningLockUtil } from './RunningLockUtil';
class UserIdleTask {
  private static subscriber: Nullable<commonEventManager.CommonEventSubscriber> = undefined;
  public static async useRunningLock() : Promise<void> {
    if (UserIdleTask.subscriber === undefined) {
      UserIdleTask.subscriber = await CommonEventHelper.subscribeSystemCommonEvent(
      {
        events: [
          commonEventManager.Support.COMMON_EVENT_ENTER_FORCE_SLEEP,
          commonEventManager.Support.COMMON_EVENT_EXIT_FORCE_SLEEP,
        ],
      },
      UserIdleTask.onReceiveEvent
    );
    }
    RunningLockUtil.holdRunningLock();
    // do your task
    RunningLockUtil.unholdRunningLock();
  }

  private static onReceiveEvent(data: commonEventManager.CommonEventData) : void {
    if (data?.event === commonEventManager.Support.COMMON_EVENT_ENTER_FORCE_SLEEP) {
      RunningLockUtil.unholdRunningLock();
    }
    if (data?.event === commonEventManager.Support.COMMON_EVENT_EXIT_FORCE_SLEEP) {
      let needReholdLock = false; // make your own decision
      if (needReholdLock) {
        RunningLockUtil.holdRunningLock();
        // do your task
        RunningLockUtil.unholdRunningLock();
      }
    }
  }
}
```
