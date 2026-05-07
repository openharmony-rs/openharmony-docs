# Preventing the Idle System from Entering Sleep Mode

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @w_Machine_cc-->

## When to Use

When the PC does not detect any user activity (such as keyboard or mouse input) within a specified period, the system automatically enters sleep mode. In this case, **RunningLockType.BACKGROUND_USER_IDLE** is used to prevent the system from automatically entering sleep mode, ensuring that services are running properly.

## Environment Setup

### Environment Requirements

- Development tool and configuration:

  [DevEco Studio](https://developer.huawei.com/consumer/en/download/) is the recommended IDE for developing OpenHarmony applications. You can use this tool to develop, debug, and package applications. Download and install the tool, and verify basic operations by referring to [Creating a Project](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-create-new-project) in [Overview](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-tools-overview) to ensure that the DevEco Studio can run properly.


- SDK version configuration:
  The **RunningLockType.BACKGROUND_USER_IDLE** can be used only when the SDK version is API version 23 or later.


- HDC configuration:

  HarmonyOS Device Connector (hdc) is a command-line tool for debugging. It can be used to interact with real devices or the Emulators on Windows, Linux, and macOS. For details about the configuration, see [hdc](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/hdc).

### Setting Up the Environment

- Install [DevEco Studio](https://developer.huawei.com/consumer/en/download/deveco-studio) 4.1 or later on the PC.
- Update the public SDK to API version 23 or later. For details, see [Switching to Full SDK](https://gitee.com/openharmony/docs/blob/master/en/application-dev/faqs/full-sdk-switch-guide.md).
- Install hdc on the PC. You can use it to interact with a real device or the Emulator on Windows, Linux, or macOS.
- Use a USB cable to connect a device to the PC.

## How to Develop

### Available APIs

1. Auto sleep and forced sleep:

   Sleep refers to a low-power state in which most hardware components of a PC system stop working, and only the minimum necessary components remain running to maintain the system state. System sleep is classified into the following types:

   (1) Auto sleep: a sleep state that is automatically triggered by preset conditions or user configurations. Generally, when the system does not detect any user activity (such as keyboard or mouse input) within a specified period, the system automatically enters sleep state.

   (2) Forced sleep: a sleep state in which the system is directly instructed by the user or application to enter sleep state immediately (for example, the user closes the laptop lid or clicks the sleep button in the menu), regardless of the current system state or user activities.

2. Constraints and device differences of the **RunningLockType.BACKGROUND_USER_IDLE** API:

   (1) This type of running lock is available for both system applications and non-system applications on PCs, as well as for system applications only on non-PC devices. For non-system applications on non-PC devices, this type of running lock does not take effect. This constraint must be considered during development.

   (2) The **BACKGROUND_USER_IDLE** running lock can prevent the system from automatically sleeping, but cannot prevent the system from forcibly sleeping. Therefore, the application that uses this API must listen for the [COMMON_EVENT_ENTER_FORCE_SLEEP](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12) event and release the lock within 1 second after receiving this common event. Then it should determine whether to listen for the [COMMON_EVENT_EXIT_FORCE_SLEEP](../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_exit_force_sleep12) event and hold the lock again based on the specific scenario.
   > **NOTE**
   > 
   > When the system enters the forced sleep mode, the **BACKGROUND_USER_IDLE** lock will be forcibly released to ensure that the system can enter the sleep state. The common event provides a way for the service side to detect the forced sleep state and process the corresponding service.


### How to Develop

Use the **RunningLockType.BACKGROUND_USER_IDLE** running lock. The following is a development example:

1. Request the ohos.permission.RUNNING_LOCK permission required for using the running lock. For details about how to request permissions, see [Workflow for Requesting Permissions](../../../security/AccessToken/determine-application-mode.md).

2. Import the related modules.

   ``` TypeScript
   // Import the runningLock and commonEventManager modules.
   import { runningLock } from '@kit.BasicServicesKit';
   import { commonEventManager } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

3. Develop the common event utility class and running lock utility class.

   ``` TypeScript
   // CommonEventHelper.ets
   import { commonEventManager } from '@kit.BasicServicesKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   type SubscriberInfo = commonEventManager.CommonEventSubscribeInfo;
   type Subscriber = commonEventManager.CommonEventSubscriber;
   type EventData = commonEventManager.CommonEventData;
   
   // Common event utility class, which is used to create common event listeners and subscribe to and unsubscribe from common events.
   export class CommonEventHelper {
     // Create a listener and subscribe to a common event.
     public static async subscribeSystemCommonEvent(info: SubscriberInfo,
       callback: (data: EventData) => void): Promise<Subscriber | undefined> {
       try {
         // Create a subscriber.
         const subscriber: Subscriber = await commonEventManager.createSubscriber(info);
         // Subscribe to a specified common event.
         commonEventManager.subscribe(subscriber, (err: BusinessError, data: EventData): void => {
           if (err) {
             console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
             return;
           }
           // Execute the callback after a common event is listened for.
           callback(data);
         });
         // Return the subscriber.
         return subscriber;
       } catch (error) {
         console.error('Failed to subscribe system common event, err: ' + error);
         return undefined;
       }
     }
     
     // Unsubscribe from a common event based on the input listener.
     public static async unsubscribeSystemCommonEvent(subscriber: Subscriber | undefined): Promise<boolean> {
       try {
         // Unsubscribe from the common event.
         commonEventManager.unsubscribe(subscriber, (error: BusinessError): void => {
           if (error) {
             console.error(`Failed to unsubscribe. Code is ${error.code}, message is ${error.message}`);
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
   ```
   
   ``` TypeScript
   // RunningLockUtil.ets
   import { runningLock } from '@kit.BasicServicesKit';

   // Running lock utility class, which is used to create, hold, and release a lock.
   export class RunningLockUtil {
     // Save the running lock object.
     public static recordLock: runningLock.RunningLock | undefined;

     public static holdRunningLock(): void {
       // Use the isSupport API to check whether the current device supports the specified lock type.
       if (!runningLock.isSupported(runningLock.RunningLockType.BACKGROUND_USER_IDLE)) {
           console.error('type BACKGROUND_USER_IDLE is not support in the device.');
           return;
       }
       if (RunningLockUtil.recordLock) {
         try {
           // The lock holding duration depends on the specific service scenario. The lock is automatically released when it times out. In this example, the lock is held for 5000 ms.
           RunningLockUtil.recordLock.hold(5000);
           console.info('hold running lock success');
         } catch (err) {
           console.error('hold running lock failed, err: ' + err);
         }
       } else {
         // Create a running lock and hold it.
         RunningLockUtil.createRunningLockAndHold();
       }
     }

     private static async createRunningLockAndHold(): Promise<void> {
       try {
         const lock = await runningLock.create(
           'running_lock_user_idle',
           runningLock.RunningLockType.BACKGROUND_USER_IDLE
         );
         console.info('create running lock: ' + lock);
         RunningLockUtil.recordLock = lock;
         // The lock holding duration depends on the specific service scenario. The lock is automatically released when it times out. In this example, the lock is held for 5000 ms.
         lock.hold(5000);
         console.info('hold running lock success');
       } catch (err) {
         console.error('create or hold failed, err: ' + err);
       }
     }
   
     public static unholdRunningLock(): void {
       if (!RunningLockUtil.recordLock) {
         console.error('lock is null');
         return;
       }
       try {
         // Check whether the lock is held and release the lock.
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

4. Implement idle tasks of the background system required by services.
   ``` TypeScript
   // UserIdleTask.ets
   import { CommonEventHelper } from './CommonEventHelper';
   import { RunningLockUtil } from './RunningLockUtil';
   import { commonEventManager } from '@kit.BasicServicesKit';
   
   // Idle task class. For details, see the following steps.
   class UserIdleTask {
     private static subscriber: Nullable<commonEventManager.CommonEventSubscriber> = undefined;
     
     // 1. Initialize the common event listening and other service processes. This example only completes the listening.
     public async init(): Promise<void> {
       if (UserIdleTask.subscriber === undefined) {
         // Listen for the common events of entering and exiting the forced sleep mode, and save the subscriber.
         UserIdleTask.subscriber = await CommonEventHelper.subscribeSystemCommonEvent(
           {
             events: [
               commonEventManager.Support.COMMON_EVENT_ENTER_FORCE_SLEEP,
               commonEventManager.Support.COMMON_EVENT_EXIT_FORCE_SLEEP,
             ],
           },
           this.onReceiveEvent
         );
       }
     }
     
     // 2. Execute the task after the lock is held. After the task is complete, release the lock.
     public runUserIdleTask(): void {
       RunningLockUtil.holdRunningLock();
       // The implementation is empty in this example. You need to implement the service logic for executing idle tasks based on your requirements.
       console.info('background user idle task run');
       RunningLockUtil.unholdRunningLock();
     }
     
     // 3. Implement the callback function for receiving the common event of entering or exiting the forced sleep mode.
     private onReceiveEvent(data: commonEventManager.CommonEventData): void {
       if (data?.event === commonEventManager.Support.COMMON_EVENT_ENTER_FORCE_SLEEP) {
         // After receiving the common event indicating that the system enters the forced sleep mode, suspend or stop the task (if any) within 1s, and then release the lock.
         RunningLockUtil.unholdRunningLock();
       }
       if (data?.event === commonEventManager.Support.COMMON_EVENT_EXIT_FORCE_SLEEP) {
         // After receiving the common event indicating that the system exits the forced sleep mode, the service determines whether to continue the unfinished task (if any). In this example, no operation is performed.
       }
     }
   }
   
   // Create and execute a task.
   function main() {
     let task: UserIdleTask = new UserIdleTask();
     task.init();
     task.runUserIdleTask();
   }
   ```
