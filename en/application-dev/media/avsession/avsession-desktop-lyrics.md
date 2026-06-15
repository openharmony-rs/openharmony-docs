# Application Access to Lyrics Component

<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend@devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:21:17.579Z pushedAt=2026-06-03T09:59:17.932Z -->

Starting from API version 23, the system provides the lyrics component feature. The lyrics component is displayed on the system desktop in the form of a floating window, supporting operations such as lyrics content display, component hiding, and component locking. Custom style settings for the component by applications are not supported currently. This document describes the development steps for an application to access the lyrics component.

## How to Develop

1. Call the [isDesktopLyricSupported](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessionisdesktoplyricsupported23) API to determine whether the system/device supports the lyrics component capability. If **true** is returned, the lyrics component capability is supported.

2. Create an [AVSession instance](../avsession/avsession-access-scene.md#creating-avsession), and fill in the lyrics data in LRC format through [setting metadata](../avsession/avsession-access-scene.md#setting-metadata), including time tags and the corresponding lyrics text. For lyrics data that does not conform to the LRC format, the system may experience parsing exceptions, resulting in the inability to display the lyrics content.

3. Call the [enableDesktopLyric](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#enabledesktoplyric23) API to enable it. You need to pass in the parameter **true** to turn on the lyrics component.

4. After the lyrics component is enabled, it is hidden (not displayed) by default. The application can actively show or hide the lyrics component through the following APIs:

   **Set visibility:** Call the [setDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricvisible23) API to set whether the lyrics component is displayed.

   **Query visibility:** Call the [isDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#isdesktoplyricvisible23) API to query whether the current lyrics component is displayed.

5. After the lyrics component is enabled, it is unlocked by default. The application can actively lock or unlock the lyrics component through the following APIs:

   **Set the locked state:** Call the [setDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricstate23) API to set whether the lyrics window is locked (restricting operations such as dragging and setting the lyrics window).

   **Query the locked state:** Call the [getDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#getdesktoplyricstate23) API to query the current locked state of the lyrics component.

6. The application can listen for changes in the visibility and locked state of the lyrics component through the callbacks provided by the system. The specific APIs are as follows:

   **Listen for whether the lyrics component is visible:** Listen to [onDesktopLyricVisibilityChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ondesktoplyricvisibilitychanged23). The callback returns **false**, indicating that the current lyrics component is invisible; the callback returns **true**, indicating that the current lyrics component is visible. To cancel this listening, use the [offDesktopLyricVisibilityChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#offdesktoplyricvisibilitychanged23) API.

   **Listen for whether the lyrics component is locked:** Listen to [onDesktopLyricStateChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ondesktoplyricstatechanged23). The callback returns **false**, indicating that the current lyrics component is unlocked; the callback returns **true**, indicating that the current lyrics component is locked. To cancel this listening, use the [offDesktopLyricStateChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#offdesktoplyricstatechanged23) API.

   > **NOTE**
   >
   > Ensure that the AVSession object is not reclaimed by the system or actively released by the application during background playback. Otherwise, the lyrics component may behave abnormally.

   <!-- @[setAVSessionInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/DesktopLyric.ets) -->

   ``` TypeScript
   import { avSession as AVSessionManager } from '@kit.AVSessionKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'hello world';
     // ...
   
     build() {
       Column() {
         // ...
         Text(this.message)
           .onClick(async () => {
             console.info(`DesktopLyric set start`);
             let context = this.getUIContext().getHostContext() as Context;
             // Assume that a session has been created. For details about how to create a session, refer to the previous case.
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', 'audio');
   
             // Check whether the system supports the lyrics component
             let isDesktopLyricSupported: boolean = false;
             try {
               isDesktopLyricSupported = await AVSessionManager.isDesktopLyricSupported();
             } catch (err) {
               console.error(`Failed to get isDesktopLyricSupported. Code: ${err.code}, message: ${err.message}`);
             }
             if (!isDesktopLyricSupported) {
               return;
             }
   
             try {
               // Enable the lyrics component
               await session.enableDesktopLyric(true);
             } catch (err) {
               console.error(`enableDesktopLyric err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Listen for whether the lyrics component is displayed
               session.onDesktopLyricVisibilityChanged((isVisible: boolean) => {
                 console.info(`onDesktopLyricVisibilityChanged changed: ${isVisible}`)
               });
             } catch (err) {
               console.error(`onDesktopLyricVisibilityChanged err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Listen for the locked status of the lyrics component
               session.onDesktopLyricStateChanged((state) => {
                 console.info(`onDesktopLyricStateChanged changed: ${state.isLocked}`)
               });
             } catch (err) {
               console.error(`onDesktopLyricStateChanged err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Show or hide the lyrics component. The lyrics component is hidden by default after being enabled.
               await session.setDesktopLyricVisible(true);
             } catch (err) {
               console.error(`setDesktopLyricVisible err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Lock or unlock the lyrics component. The lyrics component is unlocked by default after being enabled.
               await session.setDesktopLyricState({isLocked: true});
             } catch (err) {
               console.error(`setDesktopLyricState err. Code: ${err.code}, message: ${err.message}`);
             }
   
             console.info(`DesktopLyric set done`);
           })
       }
       .width('100%')
       .height('100%')
     }
   }
   ```