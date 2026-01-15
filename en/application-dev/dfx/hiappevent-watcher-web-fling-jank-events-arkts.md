# Subscribing to ArkWeb Fling Jank Events (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @pxlstrong-->
<!--Designer: @pxlstrong-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Introduction

This topic describes how to subscribe to ArkWeb fling jank events by using the ArkTS APIs provided by HiAppEvent. For details about how to use the APIs (such as parameter restrictions and value ranges), see [@ohos.hiviewdfx.hiAppEvent (Application Event Logging)](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

## Available APIs

| API| Description|
| -------- | -------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | Adds a watcher to subscribe to the application event.|
| removeWatcher(watcher: Watcher): void | Removes a watcher to unsubscribe from the application event.|

## How to Develop
The following walks you through on how to subscribe to the ArkWeb fling jank events.

1. Create a project in DevEco Studio and select **Empty Ability**. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, import the dependent modules.

   <!-- @[ArkWeb_Fling_Jank_ArkTS_Add_Watcher_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // This variable is defined in the /pages/ArkWebPage.ets file and is used to map webId to the web page URL.
   import { webIdToUrlMap } from '../pages/ArkWebPage';
   ```

2. In the **entry/src/main/ets/entryability/EntryAbility.ets** file of the project, add a watcher in **onCreate()** to subscribe to system events. The sample code is as follows:

   <!-- @[ArkWeb_Fling_Jank_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // Add a watcher to subscribe to the ArkWeb fling jank events.
   hiAppEvent.addWatcher({
     // Set the watcher name. The system identifies different watchers based on their names.
     name: 'webJankwatcher',
     // Add the system events to watch, for example, ArkWeb fling jank events.
     appEventFilters: [
       {
         domain: hiAppEvent.domain.OS,
         names: [hiAppEvent.event.SCROLL_ARKWEB_FLING_JANK]
       }
     ],
     // Implement a callback for the registered system event so that you can apply custom processing to the event data obtained.
     onReceive: (domain: string, appEventGroups: Array<hiAppEvent. AppEventGroup>) => {
       hilog.info(0x0000, 'testTag', `HiAppEvent onReceive: domain=${domain}`);
       for (const eventGroup of appEventGroups) {
         // The event name uniquely identifies a system event.
         hilog.info(0x0000, 'testTag', `HiAppEvent eventName=${eventGroup.name}`);
         for (const eventInfo of eventGroup.appEventInfos) {
           // Apply custom processing to the event data obtained, for example, print the event data in the log.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.domain=${eventInfo.domain}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.name=${eventInfo.name}`);
           // Obtain the timestamp when the fling jank event starts.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.start_time=${eventInfo.params['start_time']}`);
           // Obtain the duration of the fling effect.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.duration=${eventInfo.params['duration']}`);
           // Obtain the ID of the web page where the jank event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.web_id=${eventInfo.params['web_id']}`);
           // Obtain the maximum duration of frame loss during the fling phase.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.max_app_frame_time=${eventInfo.params['max_app_frame_time']}`);
           const webId: number = eventInfo.params['web_id'];
           // webIdToUrlMap is a variable defined to map webId to URL. You can query the web page where frame loss occurs based on web_id obtained from the system.
           const currentUrl = webIdToUrlMap.get(webId);
           // Obtain the page where the jank event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent get currentUrl=${currentUrl}`);
         }
       }
     }
   });
   ```

3. Add the **ArkWebPage.ets** file to the **entry/src/main/ets/pages** directory of the project, load the web page under **build**, and periodically deliver time-consuming tasks to block the application main thread and trigger frame loss. The sample code is as follows:

   <!-- @[ArkWeb_Fling_Jank_Page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/ArkWebPage.ets) -->
   
   ``` TypeScript
   import web_webview from '@ohos.web.webview';
   
   // Used to store the mapping between web_id and URL.
   export const webIdToUrlMap = new Map<number, string>();
   
   @Entry
   @Component
   struct ArkWebPage {
     controller = new web_webview.WebviewController();
   
     build() {
       Column() {
         Web({ src: 'https://baidu.com',
           controller: this.controller
         })
           .height('100%')
           .onPageBegin((event) => {
             // Each time a new page is displayed, the mapping between webId and URL is updated so that the web page where frame loss occurs can be queried based on web_id provided by the system.
             if (event) {
               const newUrl = event.url;
               const webId = this.controller.getWebId();
               webIdToUrlMap.set(webId, newUrl);
             }
           })
           .onPageEnd(() => {
             // Block the application main thread for 200 ms every 2s.
             setInterval(() => {
               const endTime = Date.now() + 200;
               while (Date.now() < endTime) {}
             }, 2000);
           })
       }
     }
   }
   ```

   > **NOTE**
   >
   > To include multiple web pages on a page, create multiple **WebView** components, so that each **WebView** component loads a web page.

4. In the **entry/src/main/ets/pages/Index.ets** file in the project, add a button, and redirect to the web page in the **onClick** function of the button. The sample code is as follows:
 
   <!-- @[ArkWeb_Fling_Jank_ArkTs_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Click the button to redirect to the web page where frame loss easily occurs, triggering the ArkWeb fling jank event.
   Button('ArkWebFlingJank ArkTs')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       router.pushUrl({url: 'pages/ArkWebPage'});
     })
   ```

5. In the **entry/src/main/resources/base/profile/main_pages.json** file of the project, configure the **ArkWebPage** routing page.

   ```json
   {
     "src": [
       "pages/Index",
       "pages/ArkWebPage"
     ]
   }
   ```

6. In the **entry/src/main/module.json5** file of the project, add the network access permission.

   <!-- @[ArkWeb_Fling_Jank_NetWork](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/module.json5) -->
   
   ``` JSON5
   "requestPermissions": [
     {
       "name": "ohos.permission.INTERNET"
     }
   ],
   ```

   > **NOTE**
   >
   > For details about how to use **Web** components, see [About This Kit](../web/web-component-overview.md).

7. Click the **Run** button in DevEco Studio to run the project. Then, click **ArkWebFlingJank ArkTs** on the application page to go to the web page. After the page is loaded, scroll the page to trigger the ArkWeb fling jank event.

8. If the frame freezing duration during each fling is 50 ms or longer, you can view the processing logs of the system event in the **Log** window.

   ```text
   HiAppEvent eventInfo.domain=OS
   HiAppEvent eventInfo.name=SCROLL_ARKWEB_FLING_JANK
   HiAppEvent eventInfo.params.start_time=1765892111768
   HiAppEvent eventInfo.params.duration=1554
   HiAppEvent eventInfo.params.web_id=1
   HiAppEvent eventInfo.params.max_app_frame_time=195
   HiAppEvent get currentUrl=https://www.baidu.com
   ```
