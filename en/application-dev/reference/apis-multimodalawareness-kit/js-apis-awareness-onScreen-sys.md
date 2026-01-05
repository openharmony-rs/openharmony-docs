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

## Scenario

Enumerates the scenarios of the onscreen content.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| UNKNOWN | 0    | Unknown scenario.|
| ARTICLE | 1    | Article scenario.|

## EventType

Enumerates the control event types.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| SCROLL_TO_HOOK  | 1    | Scrolling to the hook.|

## Paragraph

Defines the paragraph information.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| hookId   | number | No  | Yes  | Hook ID of the paragraph, which is the identifier of each main paragraph.|
| chapterId   | number | No  | Yes  | Chapter ID of the paragraph, which is the identifier of each subchapter.|
| title    | string | No  | Yes  | Title of the paragraph.|
| text    | string | No  | Yes  | Content of the paragraph.|

## ContentOptions

Defines the options for obtaining the onscreen content.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | Yes  | ID of the window whose content needs to be obtained. If this parameter is not set or is set to **undefined**, the content of the full-screen window is obtained by default.|
| contentUnderstand   | boolean | No  | Yes  | Whether content understanding is required. The default value is **False**.|
| pageLink    | boolean | No  | Yes  | Whether to obtain the page link. The default value is **False**.|
| textOnly    | boolean | No  | Yes  | Whether to obtain only the text and divide the text into paragraphs. The default value is **False**.|

## PageContent

Defines the onscreen content.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | No  | Window ID of the onscreen content.|
| sessionId   | number | No  | No  | Session ID, which identifies the call action.|
| bundleName    | string | No  | No  | Bundle name of the onscreen content.|
| scenario    | [Scenario](#scenario) | No  | Yes  | Scenario of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.|
| title    | string | No  | Yes  | Title of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.|
| content    | string | No  | Yes  | Body of the onscreen content. This parameter is available only when **options.contentUnderstand** is set to **True**.|
| pageLink    | string | No  | Yes  | Page link of the onscreen content. This parameter is available only when **options.pageLink** is set to **True**.|
| paragraphs    | [Paragraph](#paragraph)[] | No  | Yes  | Paragraph information of the onscreen content. This parameter is available only when **options.textOnly** is set to **True**.|

## ControlEvent

Defines a control event.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | No  | ID of the window to be operated.|
| sessionId   | number | No  | No  | ID of the session to be operated. The hook ID and the session ID can be obtained from [PageContent](#pagecontent) of a session.|
| eventType    | [EventType](#eventtype) | No  | No  | Control event type.|
| hookId    | number | No  | Yes  | Hook ID corresponding to the control event. The hook ID and the session ID can be obtained from [PageContent](#pagecontent) of a session.|

## OnscreenAwarenessCap<sup>23+</sup>

Defines onscreen awareness capabilities (including awareness in a reading scenario and OCR).

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| capList   | string[] | No  | No  | Capability list, including the capabilities for obtaining page content, page link, and text selection information. |

|**Capability**|**Function**|
| ---- | ------ |
|contentUiTree|Obtains component tree information.|
|contentUiOcr|Obtains OCR information.|
|contentScreenshot|Obtains screenshot information.|
|contentLink|Obtains a page revisit link.|
|contentUiTreeWithImage|Obtains component tree information and image information in a component.|
|interactionTextSelection|Obtains text selection information.|
|interactionClick|Obtains a click event and component node information.|
|interactionScroll|Obtains a scroll event and component node information.|
|scenarioReading|Obtains the information about awareness in a reading scenario.|
|scenarioShortVideo|Obtains the information about awareness in a short video scenario.|
|scenarioTodo|Obtains the information about awareness in a to-do scenario.|

## OnscreenAwarenessOptions<sup>23+</sup>

Defines the list of onscreen awareness parameters, which is used to obtain onscreen information in specific scenarios. For example, a window ID is provided to collect application UI content and links.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| parameters   | Record&lt;string, Object&gt; | No  | Yes  | List of awareness parameters. The parameter result is a key-value data object.|

## CollectStrategy<sup>23+</sup>

Defines a page information collection policy.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| ALLOW | 1 << 0    | Collection is supported.|
| SPLIT_SCREEN | 1 << 1    | Collection policy of the split-screen window on the application.|
| UNSUPPORTED_APP | 1 << 2  | The collection is not supported by the application.|
| PRIVATE_WINDOW | 1 << 3  | Privacy window of the application.|
| VM_APP | 1 << 4 | VM application, which is a non-HarmonyOS application.|

## EntityInfo<sup>23+</sup>

Provides entity information perceived, including content, links, images, and other types of entities.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| entityName   | string | No  | No  | Name of the perceived entity, which is fixed.|
| entityInfo   | Record<string, Object> | No  | No  | Entity information perceived , including content, links, images, and other types of entities.|


## OnscreenAwarenessInfo<sup>23+</sup>

Returns the list of onscreen awareness information.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| resultCode  | number | No  | No  | Return code. The default value **0** indicates success.|
| timestamp   | number | No  | No  | Timestamp for accessing a specified page.|
| bundleName  | string | No  | Yes  | Application bundle name.|
| appID      | string | No  | Yes  | Applet ID, for example, the ID of WeChat or Alipay.|
| appIndex   | number | No  | Yes  | Application index.|
| pageId     | string | No  | Yes  | Application page ID.|
| sampleId   | string | No  | Yes  | Collection record ID.|
| collectStrategy   | number | No  | Yes  | Page collection policy, which is the bitwise OR operation combination of [CollectStrategy](#collectstrategy23).|
| displayId   | number | No  | Yes  | Display ID.|
| windowId    | number | No  | Yes  | Window ID.|
| entityInfo  | [EntityInfo](#entityinfo23)[] | No  | Yes  | Entity information.|

## ReadingScreenPermissionStatus<sup>23+</sup>

Returns the status of the permission for reading screen information.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name| Type  | Read-Only| Optional| Description                                    |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| readingState  | number | No  | No  | Whether screen reading is allowed.<br>**0**: no<br>**1**: yes|
| readingCode   | number | No  | No  | If the screen information cannot be read, the corresponding status code will be returned.|


## onScreen.getPageContent

getPageContent(options?: [ContentOptions](#contentoptions)): Promise&lt;[PageContent](#pagecontent)&gt;

Obtains the onscreen content when a window is displayed on the screen.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| options | [ContentOptions](#contentoptions)   | No  | Options for obtaining the onscreen screen content. By default, the window ID is not specified, and other options are **False**.|

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

sendControlEvent(event: [ControlEvent](#controlevent)): Promise&lt;void&gt;

If the target window is displayed on the screen, you can use this API to send screen control events based on the paragraph information obtained via [onScreen.getPageContent](#onscreengetpagecontent).

**Required permissions**: ohos.permission.SIMULATE_USER_INPUT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| event | [ControlEvent](#controlevent)   | Yes  | Onscreen control event.|

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
         if (pageContent.paragraphs != undefined && pageContent.paragraphs.length > 0 &&
            pageContent.paragraphs[0].hookId != undefined) {
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

## onScreen.subscribe<sup>23+</sup>
subscribe(capability: OnscreenAwarenessCap, 
          callback: Callback&lt;OnscreenAwarenessInfo&gt;, 
          options?: OnscreenAwarenessOptions): void

Enables proactive awareness on screen content and subscribes to a screen awareness result.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 801 is returned.

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes  | Onscreen awareness capability list.|
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| No  | Onscreen awareness parameter list.|
| callback | Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | Yes  | Callback function, which returns the onscreen awareness result.|


**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**Example**

   ```ts
   import onScreen from "@ohos.multimodalAwareness.onScreen";
   let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
      capList: [
         'contentUiTree',
         'scenarioReading'
      ],
      description: 'reading scenario'
   }

   let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
      parameters: {
         "windowId": 12,
         "controlByPolicy": 1
      } as Record<string, Object>
   }

   try {
      onScreen.subscribe(onscreenAwarenessCap, (info: onScreen.OnscreenAwarenessInfo) => {
         console.info(`subscribe resultCode: ${info.resultCode}`);
      }, onscreenAwarenessOptions);
   } catch (err) {
      console.error('subscribe failed, errCode = ' + err.code);
   }
   ```
## onScreen.unsubscribe<sup>23+</sup>

unsubscribe(capability: OnscreenAwarenessCap, 
            callback?: Callback&lt;OnscreenAwarenessInfo&gt;): void

Disables proactive awareness on screen content and unsubscribes from a screen awareness result.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 801 is returned.

**Parameters**

| Name  | Type                            | Mandatory| Description              |
| -------- | -------------------------------- | ---- | ---------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes  | Onscreen awareness capability list.|
| callback | Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | Yes  | Callback to unregister. If this parameter is not passed, all callbacks of the awareness capability are unregistered.|

**Error codes**

For details about the error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**Example**

```ts
import onScreen from "@ohos.multimodalAwareness.onScreen";
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
	'contentUiTree',
  ],
  description: 'unsubscribe uiTree scenario'
}

try {
  onScreen.unsubscribe(onscreenAwarenessCap, (info: onScreen.OnscreenAwarenessInfo) => {
	console.info(`unsubscribe resultCode: ${info.resultCode}`);
  });
} catch (err) {
  console.error('unsubscribe failed, errCode = ' + err.code);
}
```

## onScreen.trigger<sup>23+</sup>

trigger(capability: OnscreenAwarenessCap, 
        options?: OnscreenAwarenessOptions): Promise&lt;OnscreenAwarenessInfo&gt;

Proactively triggers screen content awareness and obtains the current screen awareness result.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 801 is returned.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes  | Onscreen awareness capability list.|
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| No  | Onscreen awareness parameter list.|


**Return value**

  | Type                          | Description        |
  | ---------------------------- | ---------- |
  | Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | Promise used to return the onscreen awareness result.|
**Error codes**

For details about the error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**Example**

```ts
import onScreen from "@ohos.multimodalAwareness.onScreen";
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'contentUiTree',
    'scenarioReading'
  ],
  description: 'subscribe reading scenario'
}

let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
  parameters: {
    "windowId": 12,
    "controlByPolicy": 1
  } as Record<string, Object>
}
try {
  let info: onScreen.OnscreenAwarenessInfo =
    await onScreen.trigger(onscreenAwarenessCap, onscreenAwarenessOptions);
  console.info(`trigger resultCode: ${info.resultCode}`);
} catch (err) {
  console.error('trigger failed, errCode = ' + err.code);
}
```

## onScreen.onReadingScreenPermissionListener<sup>23+</sup>

onReadingScreenPermissionListener(callback: Callback&lt;ReadingScreenPermissionStatus&gt;): void

Enables the screen content access permission monitoring and returns the permission status in real time.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 801 is returned.

**System API**: This is a system API.

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[ReadingScreenPermissionStatus](#readingscreenpermissionstatus23)&gt; | Yes  | Callback used to return the status of the permission for reading screen information.|


**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**Example**

```ts
import onScreen from "@ohos.multimodalAwareness.onScreen";
try {
   onScreen.onReadingScreenPermissionListener((info: onScreen.ReadingScreenPermissionStatus) => {
      console.info(`onReadingScreenPermissionListener succeeded, readingState: ${info.readingState}`);
   });
} catch (err) {
   console.error('onReadingScreenPermissionListener failed, errCode = ' + err.code);
}
```

## onScreen.offReadingScreenPermissionListener<sup>23+</sup>

offReadingScreenPermissionListener(callback?: Callback&lt;ReadingScreenPermissionStatus&gt;): void

Disables the screen content access permission monitoring.

**Required permissions**: ohos.permission.GET_SCREEN_CONTENT.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences**: This API can be properly called on phones and tablets. If it is called on other devices, error code 801 is returned.

**Parameters**

| Name  | Type                            | Mandatory| Description              |
| -------- | -------------------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;[ReadingScreenPermissionStatus](#readingscreenpermissionstatus23)&gt; | Yes  | Callback to unregister. If this parameter is not passed, all callbacks of the event are unregistered.|

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**Example**

```ts
import onScreen from "@ohos.multimodalAwareness.onScreen";
try {
  onScreen.offReadingScreenPermissionListener();
  console.info(`offReadingScreenPermissionListener succeeded.`);
} catch (err) {
  console.error('offReadingScreenPermissionListener failed, errCode = ' + err.code);
}
```
