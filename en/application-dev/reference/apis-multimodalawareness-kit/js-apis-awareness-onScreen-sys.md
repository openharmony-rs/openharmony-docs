# @ohos.multimodalAwareness.onScreen (Onscreen Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

This module provides the onscreen awareness capability.

> **NOTE**
>
> 1. The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 2. The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## onScreen.Scenario

Enumerates the scenarios of the onscreen content.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| UNKNOWN | 0    | Unknown scenario.|
| ARTICLE | 1    | Article scenario.|

## onScreen.EventType

Enumerates the control event types.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| SCROLL_TO_HOOK  | 1    | Scrolling to the hook.|

## onScreen.Paragraph

Defines the paragraph information.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| hookId   | number | No  | Yes  | Hook ID of the paragraph, which is the identifier of each main paragraph.|
| chapterId   | number | No  | Yes  | Chapter ID of the paragraph, which is the identifier of each subchapter.|
| title    | string | No  | Yes  | Title of the paragraph.|
| text    | string | No  | Yes  | Content of the paragraph.|

## onScreen.ContentOptions

Defines the options for obtaining the onscreen content.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | Yes  | ID of the window whose content needs to be obtained. If this parameter is not set or is set to **undefined**, the content of the full-screen window is obtained by default.|
| contentUnderstand   | boolean | No  | Yes  | Whether content understanding is required. The default value is **False**.|
| pageLink    | boolean | No  | Yes  | Whether to obtain the page link. The default value is **False**.|
| textOnly    | boolean | No  | Yes  | Whether to obtain only the text and divide the text into paragraphs. The default value is **False**.|

## onScreen.PageContent

Defines the onscreen content.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | No  | Window ID of the onscreen content.|
| sessionId   | number | No  | No  | Session ID, which identifies the call action.|
| bundleName    | string | No  | No  | Bundle name of the onscreen content.|
| scenario    | [Scenario](#onscreenscenario) | No  | Yes  | Scenario of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.|
| title    | string | No  | Yes  | Title of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.|
| content    | string | No  | Yes  | Body of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.|
| pageLink    | string | No  | Yes  | Page link of the onscreen content. This parameter is available only when **options.pageLink** is set to **True**.|
| paragraphs    | [Paragraph](#onscreenparagraph)[] | No  | Yes  | Paragraph information of the onscreen content. This parameter is available only when **options.textOnly** is set to **True**.|

## onScreen.ControlEvent

Defines a control event.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | No  | ID of the window to be operated.|
| sessionId   | number | No  | No  | ID of the session to be operated. The hook ID and the session ID are can be obtained from [PageContent](#onscreenpagecontent) of a session.|
| eventType    | [EventType](#onscreeneventtype) | No  | No  | Control event type.|
| hookId    | number | No  | Yes  | Hook ID corresponding to the control event. The hook ID and the session ID are can be obtained from [PageContent](#onscreenpagecontent) of a session.|

## onScreen.getPageContent

getPageContent(options?: [ContentOptions](#onscreencontentoptions)): Promise&lt;[PageContent](#onscreenpagecontent)&gt;

Obtains the onscreen content when a window is displayed on the screen.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| options | [ContentOptions](#onscreencontentoptions)   | No  | Options for obtaining the onscreen screen content. By default, the window ID is not specified, and other options are **False**.|

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |
| 34000003 | The window ID is invalid. Possible causes: 1. window id is not passed when screen is splited. 2. passed window id is not on screen or floating. |
| 34000004 | The page is not ready. |
| 34000006 | The request timed out. |

**Example**

   ```ts
   import { onScreen } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   let options: onScreen.ContentOptions = {
      contentUnderstand: true,
      pageLink: true
   };
   try {
      onScreen.getPageContent(options).then((pageContent: onScreen.PageContent) => {
         console.info("get page content succeed, bundleName = " + pageContent.bundleName);
      }).catch((err: BusinessError) => {
         console.error("get page content failed, errCode = " + err.code);
      });
   } catch (err) {
      console.error('get page content failed, errCode = ' + err.code);
   }
   ```

## onScreen.sendControlEvent

sendControlEvent(event: [ControlEvent](#onscreencontrolevent)): Promise&lt;void&gt;

If the target window is displayed on the screen, you can use this API to send screen control events based on the paragraph information obtained via [onScreen.getPageContent](#onscreengetpagecontent).

**Required permissions**: ohos.permission.SIMULATE_USER_INPUT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| event | [ControlEvent](#onscreencontrolevent)   | Yes  | Onscreen control event.|

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.SIMULATE_USER_INPUT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000005 | The target is not found. |

**Example**

   ```ts
   import { onScreen } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   let options: onScreen.ContentOptions = {
      contentUnderstand: true,
      textOnly: true
   };
   let event: onScreen.ControlEvent | undefined = undefined;
   try {
      onScreen.getPageContent(options).then((pageContent: onScreen.PageContent) => {
         if (pageContent.paragraphs.length > 0) {
            event = {
               windowId: pageContent.windowId,
               sessionId: pageContent.sessionId,
               hookId: pageContent.paragraphs[0].hookId,
               eventType: onScreen.EventType.SCROLL_TO_HOOK
            };
         }
      }).catch((err: BusinessError) => {
         console.error("get page content failed, errCode = " + err.code);
      });
   } catch (err) {
      console.error('invoke failed, errCode = ' + err.code);
   }
   if (event != undefined) {
      try {
         onScreen.sendControlEvent(event).catch((err: BusinessError) => {
            console.error("send control event failed, errCode =" + err.code);
         })
      } catch (err) {
         console.error('invoke failed, errCode = ' + err.code);
      }
   }
   ```
