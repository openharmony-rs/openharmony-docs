# Cleaning Up external_log Files (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @jiangwenhao-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=5c6e03ec7cfff0172ce10c87fa36d9c242ac74fb translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T06:41:24.028Z nl=1 -->

Starting from API version 26.0.1, you can register an external_log manager so that the application is notified to clean up files when a fault log directory in the application sandbox reaches its capacity threshold.

## Available APIs

For API usage, including parameter constraints and value ranges, see [@ohos.hiviewdfx.hiAppEvent](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

| Name | Description |
| -------- | -------- |
| registerExternalLogManager(logMngr: ExternalLogManager): void | Registers an external_log manager. |
| isExternalLogManagerRegistered(): boolean | Checks whether an external_log manager is registered. |

## Registering an external_log Manager

1. Create an ArkTS application project. Edit the **entry > src > main > ets > entryability > EntryAbility.ets** file and import the required modules:

   <!-- @[AppEvent_Crash_Click_ArkTS_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. In **entry > src > main > ets > entryability > EntryAbility.ets**, register an external_log manager in the **onCreate** function.

   <!-- @[RegisterExternalLogManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   // Define a function to delete files.
   let deleteFiles: (files: string[]) => void = (files: string[]): void => {
     for (const file of files) {
       try {
         fs.unlinkSync(file);
         hilog.info(0x0000, 'testTag', `[MyLogManager] Deleted: ${file}`);
       } catch (e) {
         hilog.info(0x0000, 'testTag', `[MyLogManager] Failed to delete: ${file}, error: ${e}`);
       }
     }
   };

   // Define the ExternalLogManager implementation.
   let myLogManager: hiAppEvent.ExternalLogManager = {
     onCapacityReached(container: hiAppEvent.ExternalLogContainer): void {
       hilog.info(0x0000, 'testTag', `[MyLogManager] Capacity threshold reached, log count: ${container.getLogNumber()}`);

       // Obtain all log file paths.
       let allFiles: Set<string> = container.getAllLogFiles();
       hilog.info(0x0000, 'testTag', `[MyLogManager] All log files: ${JSON.stringify(Array.from(allFiles))}`);

       // Obtain details of all logs.
       let allLogs: Set<hiAppEvent.ExternalLogWrapper> = container.getAllLogs();
       for (const log of Array.from(allLogs)) {
         hilog.info(0x0000, 'testTag', `[MyLogManager] File: ${log.getFilePath()}, ` +
           `Time: ${log.getGenerationTime()}, ` +
           `Size: ${log.getSizeInKb()}KB, ` +
           `Event: ${log.getSysEvent()}`);
       }

       // Filter logs by event type.
       let crashFiles: Set<string> = container.getLogFilesOfSysEvent('APP_CRASH');
       hilog.info(0x0000, 'testTag', `[MyLogManager] APP_CRASH logs: ${JSON.stringify(Array.from(crashFiles))}`);

       // Filter by time to obtain logs generated more than 5 minutes ago.
       let timePoint = Date.now() - 5 * 60 * 1000;
       let files: Set<string> = container.getLogFilesGeneratedBefore(timePoint);
       hilog.info(0x0000, 'testTag', `[MyLogManager] Logs older than 5 minutes: ${JSON.stringify(Array.from(files))}`);

       // Filter by time to obtain logs generated within the last 5 minutes.
       files = container.getLogFilesGeneratedAfter(timePoint);
       hilog.info(0x0000, 'testTag', `[MyLogManager] Logs from the last 5 minutes: ${JSON.stringify(Array.from(files))}`);

       // Filter by size to obtain logs larger than 100 KB.
       files = container.getLogFilesLargerThan(100);
       hilog.info(0x0000, 'testTag', `[MyLogManager] Logs larger than 100 KB: ${JSON.stringify(Array.from(files))}`);

       // Filter by size to obtain logs smaller than 100 KB.
       files = container.getLogFilesSmallerThan(100);
       hilog.info(0x0000, 'testTag', `[MyLogManager] Logs smaller than 100 KB: ${JSON.stringify(Array.from(files))}`);

       // Obtain and delete the 3 oldest log files.
       files = container.getFirstGeneratedLogFiles(3);
       hilog.info(0x0000, 'testTag', `[MyLogManager] The 3 oldest logs: ${JSON.stringify(Array.from(files))}`);
       deleteFiles(Array.from(files));
     }
   };

   // Register the external_log file manager.
   try {
     hiAppEvent.registerExternalLogManager(myLogManager);
     hilog.info(0x0000, 'testTag', '[MyLogManager] ExternalLogManager registered successfully');
   } catch (e) {
     hilog.info(0x0000, 'testTag', `[MyLogManager] Registration failed: ${e.code}, ${e.message}`);
   }

   // Check whether the manager is registered.
   let registered: boolean = hiAppEvent.isExternalLogManagerRegistered();
   hilog.info(0x0000, 'testTag', `[MyLogManager] Registered: ${registered}`);
   ```

## Debugging and Verification

1. Click the run button in DevEco Studio to run the application project.

2. Search for **MyLogManager** in the HiLog window to view the logs for registering the external_log manager:

   ```text
   [MyLogManager] ExternalLogManager registered successfully
   [MyLogManager] Registered: true
   ```

3. Using [Subscribing to Crash Events (ArkTS)](hiappevent-watcher-crash-events-arkts.md) as an example, trigger an application crash once per minute until the sandbox directory reaches its capacity threshold.

4. Search for **MyLogManager** in the HiLog window to view the callback logs generated when the external_log directory reaches its capacity threshold:

   ```text
   [MyLogManager] Capacity threshold reached, log count: 11
   [MyLogManager] File: /data/storage/el2/log/hiappevent/APP_CRASH_1788340658144_14537_0.log, Time: 1788340658144, Size: 470KB, Event: APP_CRASH
   ...
   [MyLogManager] File: /data/storage/el2/log/hiappevent/APP_CRASH_1788340823716_15778_0.log, Time: 1788340823716, Size: 50KB, Event: APP_CRASH
   [MyLogManager] APP_CRASH logs: ["/data/storage/el2/log/hiappevent/APP_CRASH_1788340658144_14537_0.log",..."/data/storage/el2/log/hiappevent/APP_CRASH_1788340418807_12609_0.log"]
   [MyLogManager] Logs older than 5 minutes: ["/data/storage/el2/log/hiappevent/APP_CRASH_1788340353265_12024_0.log",..."/data/storage/el2/log/hiappevent/APP_CRASH_1788340418807_12609_0.log"]
   [MyLogManager] Logs from the last 5 minutes: ["/data/storage/el2/log/hiappevent/APP_CRASH_1788340658144_14537_0.log",...,"/data/storage/el2/log/hiappevent/APP_CRASH_1788340823716_15778_0.log"]
   [MyLogManager] Logs larger than 100 KB: ["/data/storage/el2/log/hiappevent/APP_CRASH_1788340658144_14537_0.log",...,"/data/storage/el2/log/hiappevent/APP_CRASH_1788340823714_15778_0.log"]
   [MyLogManager] Logs smaller than 100 KB: ["/data/storage/el2/log/hiappevent/APP_CRASH_1788340708211_14892_0.log","/data/storage/el2/log/hiappevent/APP_CRASH_1788340823716_15778_0.log"]
   [MyLogManager] The 3 oldest logs: ["/data/storage/el2/log/hiappevent/APP_CRASH_1788340353265_12024_0.log","/data/storage/el2/log/hiappevent/APP_CRASH_1788340362652_12116_0.log","/data/storage/el2/log/hiappevent/APP_CRASH_1788340374253_12272_0.log"]
   [MyLogManager] Deleted: /data/storage/el2/log/hiappevent/APP_CRASH_1788340353265_12024_0.log
   [MyLogManager] Deleted: /data/storage/el2/log/hiappevent/APP_CRASH_1788340362652_12116_0.log
   [MyLogManager] Deleted: /data/storage/el2/log/hiappevent/APP_CRASH_1788340374253_12272_0.log
   ```    