# Integrating the Lyrics Component

<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend@devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:20:09.482Z pushedAt=2026-07-20T13:50:12.855Z -->

Starting from API version 23, HarmonyOS provides a desktop lyrics component that displays synchronized lyrics in a floating window on the desktop. The component supports displaying lyrics, controlling its visibility, and locking or unlocking the window. Custom styling of the component is not supported. This section describes how to use the desktop lyrics component in your application.

## How to Develop

1. Call [isDesktopLyricSupported](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessionisdesktoplyricsupported23) to check whether the system/device supports the lyrics component capability. If `true` is returned, the lyrics component capability is supported.

2. Create an [AVSession instance](../avsession/avsession-access-scene.md#creating-avsession), and [set metadata](avsession-access-scene.md#setting-metadata) to fill in lyrics data in LRC format. The lyrics must contain timestamp tags and the corresponding lyric text. Lyrics that do not conform to the LRC format may not be parsed correctly and therefore might not be displayed.

3. Call [enableDesktopLyric](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#enabledesktoplyric23) to enable the lyrics component by passing `true` as the parameter.

4. After the component is enabled, it is hidden by default. You can control its visibility using the following APIs:

   **Setting visibility:** Call [setDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricvisible23) to set whether the lyrics component is displayed.

   **Querying visibility:** Call [isDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#isdesktoplyricvisible23) to query whether the lyrics component is currently displayed.

5. After the component is enabled, it is unlocked by default. You can control its lock state using the following APIs:

   **Setting the locked state:** Call [setDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricstate23) to set whether the lyrics window is locked (which restricts operations such as dragging and settings on the lyrics window).

   **Querying the locked state:** Call [getDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#getdesktoplyricstate23) to query the current locked state of the lyrics component.

6. The app can listen for changes in the visibility and locked state of the lyrics component through the callbacks provided by the system. The specific APIs are as follows:

   **Listening for whether the lyrics component is visible:** Register [onDesktopLyricVisibilityChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ondesktoplyricvisibilitychanged23). The callback returns `true` when the component is visible and `false` when it is hidden. To unregister the callback, call [offDesktopLyricVisibilityChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#offdesktoplyricvisibilitychanged23).

   **Listening for whether the lyrics component is locked:** Register [onDesktopLyricStateChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ondesktoplyricstatechanged23). The callback returns `true` when the component is locked and `false` when it is unlocked. To unregister the callback, call [offDesktopLyricStateChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#offdesktoplyricstatechanged23).

   > **NOTE**
   >
   > Ensure that the `AVSession` instance remains valid while audio playback continues in the background. If the `AVSession` instance is reclaimed by the system or released by the application, the lyrics component may not function correctly.

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
             // Assume a session has been created. For how to create a session, refer to the previous example.
             let session = await AVSessionManager.createAVSession(context, 'SESSION_NAME', 'audio');
   
             // Check whether the system supports the lyrics component.
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
               // Enable the lyrics component.
               await session.enableDesktopLyric(true);
             } catch (err) {
               console.error(`enableDesktopLyric err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Listen for whether the lyrics component is displayed.
               session.onDesktopLyricVisibilityChanged((isVisible: boolean) => {
                 console.info(`onDesktopLyricVisibilityChanged changed: ${isVisible}`)
               });
             } catch (err) {
               console.error(`onDesktopLyricVisibilityChanged err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Listen for the locked state of the lyrics component.
               session.onDesktopLyricStateChanged((state) => {
                 console.info(`onDesktopLyricStateChanged changed: ${state.isLocked}`)
               });
             } catch (err) {
               console.error(`onDesktopLyricStateChanged err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Show or hide the lyrics component. It is hidden by default after being enabled.
               await session.setDesktopLyricVisible(true);
             } catch (err) {
               console.error(`setDesktopLyricVisible err. Code: ${err.code}, message: ${err.message}`);
             }
   
             try {
               // Lock or unlock the lyrics component. It is unlocked by default after being enabled.
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