# @ohos.multimodalAwareness.onScreen (Onscreen Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=417f502e638a0076ecc77fba99d31577589d7d54 translatedAt=2026-09-14T02:10:30.510Z pushedAt=2026-09-14T10:03:33.580Z -->

This module provides the capability of apperceiving on-screen content, including obtaining page content, links, screenshots, and other information, identifying application scenarios such as reading and short video, providing entity information such as article titles and body text, as well as interaction information such as clicks and scrolling.

> **NOTE**
>
> 1. The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 2. The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## Scenario

Enumerates the scenario types of on-screen content.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

| Name | Value | Description |
| ------------------- | ---- | ---------------------- |
| UNKNOWN | 0 | The scenario of the on-screen content is unknown. |
| ARTICLE | 1 | The on-screen content is in an article scenario. |

## EventType

Enumerates the types of control events.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This API is a system API.

| Name                | Value   | Description                   |
| ------------------- | ---- | ---------------------- |
| SCROLL_TO_HOOK  | 1    | Indicates the event of scrolling to the hook point. |

## Paragraph

Paragraph information.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| hookId   | number | No   | Yes   | Hook ID corresponding to the paragraph, which identifies each main paragraph. |
| chapterId   | number | No   | Yes   | Chapter ID corresponding to the paragraph, which identifies each subchapter. |
| title    | string | No   | Yes   | Title corresponding to the paragraph. |
| text    | string | No   | Yes   | Content corresponding to the paragraph. |

## ContentOptions

Options for obtaining on-screen content.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This API is a system API.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | Yes  | Window ID of the content to be obtained. If not assigned or assigned **undefined**, the full-screen window is obtained by default. |
| contentUnderstand   | boolean | No  | Yes  | Whether to perform content understanding. The value **true** means yes, and **false** means no. The default value is **false**. |
| pageLink    | boolean | No  | Yes  | Whether to obtain the revisit link. The value **true** means to obtain it, and **false** means not to obtain it. The default value is **false**. |
| textOnly    | boolean | No  | Yes  | Whether to obtain only text and divide it into paragraphs. The value **true** means yes, and **false** means no. The default value is **false**. |

## PageContent

On-Screen Content.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No   | No   | Window ID of the obtained on-screen content. |
| sessionId   | number | No   | No   | Session ID of this API call, which identifies the current call action. |
| bundleName    | string | No   | No   | Bundle name of the obtained on-screen content. |
| scenario    | [Scenario](#scenario) | No   | Yes   | Scenario of the obtained on-screen content. This attribute is obtained only when **options.contentUnderstand** is **true**. |
| title    | string | No   | Yes   | Title of the obtained on-screen content. This attribute is obtained only when **options.contentUnderstand** is **true**. |
| content    | string | No   | Yes   | Body of the obtained on-screen content. This attribute is obtained only when **options.contentUnderstand** is **true**. |
| pageLink    | string | No   | Yes   | Revisit link of the obtained on-screen content. This attribute is obtained only when **options.pageLink** is **true**. |
| paragraphs    | [Paragraph](#paragraph)[] | No   | Yes   | Obtained text paragraph information. This attribute is obtained only when **options.textOnly** is **true**. |

## ControlEvent

Control Event.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | No  | No  | Window ID of the window to be operated by the control event. |
| sessionId   | number | No  | No  | Session ID to be operated by the control event. Both the hook ID to be operated by the control event and the session ID corresponding to this session are provided by the [PageContent](#pagecontent) obtained in a session. |
| eventType    | [EventType](#eventtype) | No  | No  | Type of the control event. |
| hookId    | number | No  | Yes  | Hook ID corresponding to the control event. Both the hook ID to be operated by the control event and the session ID corresponding to this session are provided by the [PageContent](#pagecontent) obtained in a session. |

## OnscreenAwarenessCap<sup>23+</sup>

On-screen awareness capabilities (including but not limited to reading scenario awareness, OCR recognition, and other functions).

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type   | Read Only | Optional | Description                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| capList   | string[] | No   | Yes   | Represents the capability set, including page content, page link, text selection, and other capabilities. For details about the specific capability items, see the following table.|
| groupId | string | No | Yes | Business group ID. For details about the specific group IDs, see the following table.|

Parameter constraint description:<br>
Users can use the on-screen awareness feature through capability items (**capList**) or group IDs (**groupId**).
* Logical relationship: **capList** and **groupId** are complementary required items. At least one of them must be provided and must not be empty.<br>
* Validation rule: When the API is called, the system checks capList and groupId separately.<br>
* Capability list: Use the on-screen awareness feature by capability item or group ID. The specific definitions are as follows.
  * capList Supported Capability List<br>
    Capabilities preset for specific business scenarios, which can be subscribed to or triggered individually, as follows:
    |capList Capability List|Description|
    | ---- | ------ |
    |Article|Obtains the awareness information of the reading scenario.|
    |ShortVideo|Obtains the awareness information of the short video scenario.|
    |Todo|Obtains the awareness information of the to-do scenario.|
    |Activity|Obtains the awareness information of basic services.|
    |UiImage|Obtains the sub-image information within the page.|
    |JumpContext|Highlights and jumps to the specified context.|
    |QuickSnap|Obtains single screenshot information.<br> **Usage Specification**: Takes effect only when used with the **capture** API and when **capList** passes only "QuickSnap". Other APIs return error code 401.|
    |UiTree|Obtains the JSON tree information within the page.<br> **Since:** 26.0.0|
    |InjectEvent|Injects events.<br> **Since:** 26.0.0|
    |CollectStrategy|Obtains the screen collection strategy.<br> **Since:** 26.0.0|
    |SmartAutoFill|Intelligently fills the content of the page input box.<br> **Since:** 26.0.0|
    |SmartAutoFillSwitch|Subscribes to or unsubscribes from the smart fill switch status of page content.<br> **Usage Specification**: Only the smart fill application (com.huawei.hms.textautofill) is allowed to call this API. Calling by non-trustlisted applications returns error code 34000002.<br> **Since:** 26.0.0|

  * groupId Capability List<br>
    A set of capabilities preset for business scenarios. Business scenarios can be subscribed to in a unified manner, as follows:

    |groupId Capability List|Corresponding Sub-Item Capability|Description|
    | ---- | ------ | ------|
    |SmartEdge|Article|Obtains the awareness information of the reading scenario.|
    |SmartEdge|ShortVideo|Obtains the awareness information of the short video scenario.|
    |SmartEdge|Todo|Obtains the awareness information of the to-do scenario.|
    |SmartEdge|Activity|Obtains the awareness information of basic services.|
    |CeliaMemory|Article|Obtains the awareness information of the reading scenario.|
    |SmartBar|SmartAutoFill|Intelligently fills the content of the page input box.|

## OnscreenAwarenessOptions<sup>23+</sup>

On-Screen Awareness parameter list, used to obtain on-screen information in specific scenarios, such as providing a window ID to collect application interface content and links.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type   | Read Only | Optional | Description                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| parameters   | Record&lt;string, Object&gt; | No   | Yes   | Awareness parameter list. The parameter result is a key-value data object. |

## CollectStrategy<sup>23+</sup>

Page information collection strategy.

**System capability**: SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name                | Value   | Description                   |
| ------------------- | ---- | ---------------------- |
| ALLOW | 1 << 0    | The application supports collection. |
| SPLIT_SCREEN | 1 << 1    | Collection strategy for the split-screen window of an application. |
| UNSUPPORTED_APP | 1 << 2  | The application does not support automatic collection. |
| PRIVATE_WINDOW | 1 << 3  | The privacy window of an application. |
| ANCO_APP | 1 << 4 | A virtual machine application, not a HarmonyOS application. |
| ALLOW_USER_CHANGE | 1 << 5  | The collection strategy of the application is configurable. |
| BUSINESS_APP | 1 << 6 | The application data can be collected. |
| FLOAT_SCREEN | 1 << 7  | Floating window. |
| PIP_SCREEN | 1 << 8 | Picture-in-picture mode. |
| LAUNCHER | 1 << 9 | Launcher application. |

## AwarenessItem<sup>23+</sup>

Provides page information. Including:
* Basic page information, such as page content, links, and screenshots.
* Page entity information, such as the title and body of a page article.
* Page interaction information, such as tap and scroll information.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| itemInfo | Record<string, Object> | Yes | No | Awareness result entity information, including content, links, screenshots, and other entity information. |

## EntityInfo<sup>23+</sup>

Provides the apperceived entity information, including content, links, images, and other types of entities.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| entityName   | string | Yes  | No  | Name of the entity in the awareness result. Fixed content. |
| entityInfo   | Record<string, Object> | Yes  | No  | Entity information in the awareness result, including content, links, images, and other entities.|

## OnscreenAwarenessInfo<sup>23+</sup>

List of information returned by on-screen awareness.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| resultCode  | number | Yes | No | Result code. The default value **0** indicates success. |
| timestamp   | number | Yes | No | Timestamp when entering a specific page, in ms. |
| uid   | string | Yes | Yes | Application UID. |
| bundleName  | string | Yes | Yes | Application package name. |
| appName  | string | Yes | Yes | Application name. |
| miniProgramId | string | Yes | Yes | Mini program ID, for example, the mini program ID of a third-party application such as WeChat or Alipay. |
| miniProgramName | string | Yes | Yes | Mini program name, that is, the mini program name of a third-party application. |
| appIndex   | number | Yes | Yes | Application index. |
| pageId     | string | Yes | Yes | Application page ID. |
| sampleId   | string | Yes | Yes | Collection record ID. |
| collectStrategy   | number | Yes | Yes | Page collection strategy, which is a bitwise OR combination of [CollectStrategy](#collectstrategy23). |
| displayId   | number | Yes | Yes | Screen ID. |
| windowId    | number | Yes | Yes | Window ID. |
| languageInfo | string | Yes | Yes | Page language information. |
| pageTags | string[] | Yes | Yes | Page tag information. |
| items  | [AwarenessItem](#awarenessitem23)[] | Yes | Yes | Data item information. |
| entityInfo  | [EntityInfo](#entityinfo23)[] | Yes | Yes | Entity information. |

## ReadingScreenPermissionStatus<sup>23+</sup>

Permission status for reading screen information.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read Only | Optional | Description |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| readingState  | number | Yes   | No   | Whether screen reading is allowed.<br>**0**: screen reading is not allowed.<br>**1**: screen reading is allowed. |
| readingCode   | number | Yes   | Yes  | If the screen cannot be read, the corresponding status code is returned. For details, see [CollectStrategy](#collectstrategy23). |


## onScreen.getPageContent

getPageContent(options?: [ContentOptions](#contentoptions)): Promise&lt;[PageContent](#pagecontent)&gt;

Obtains the on-screen content when the window whose content is to be captured is on the desktop.

**Required permission:** ohos.permission.GET_SCREEN_CONTENT

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| options | [ContentOptions](#contentoptions) | No | Options for obtaining the on-screen content. By default, no window ID is specified and all other options are set to **false**. |

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |
| 34000003 | The window ID is invalid. Possible causes: 1. window id is not passed when screen is split. 2. passed window id is not on screen or floating. |
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
         console.error(`get page content failed, Code: ${err.code}, message: ${err.message}`);
      });
   } catch (err) {
      console.error(`get page content failed, Code: ${err.code}, message: ${err.message}`);
   }
   ```

## onScreen.sendControlEvent

sendControlEvent(event: [ControlEvent](#controlevent)): Promise&lt;void&gt;

When the window to be controlled is on the desktop, call this API to send an on-screen control event based on the paragraph information returned by [onScreen.getPageContent](#onscreengetpagecontent).

**Required permissions:** ohos.permission.SIMULATE_USER_INPUT

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API**: This is a system API.

**Parameters**

| Name  | Type                           | Mandatory | Description                                                  |
| ----- | ------------------------------ | --------- | ------------------------------------------------------------ |
| event | [ControlEvent](#controlevent) | Yes       | On-screen control event. |

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.SIMULATE_USER_INPUT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000005 | The target is not found. |

**Example**:

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
         console.error(`get page content failed, Code: ${err.code}, message: ${err.message}`);
      });
   } catch (err) {
      console.error(`invoke failed, Code: ${err.code}, message: ${err.message}`);
   }
   if (event != undefined) {
      try {
         onScreen.sendControlEvent(event).catch((err: BusinessError) => {
            console.error(`send control event failed, Code: ${err.code}, message: ${err.message}`);
         })
      } catch (err) {
         console.error(`invoke failed, Code: ${err.code}, message: ${err.message}`);
      }
   }
   ```

## onScreen.subscribe<sup>23+</sup>

subscribe(capability: OnscreenAwarenessCap, callback: Callback&lt;OnscreenAwarenessInfo[]&gt;, options?: OnscreenAwarenessOptions): void

Enables proactive awareness of on-screen content and subscribes to the on-screen awareness result.

**Required Permission**

- API version 26+: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS.
- API version 23-24: ohos.permission.GET_SCREEN_CONTENT.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23) | Yes | On-screen awareness capability list. |
| options | [OnscreenAwarenessOptions](#onscreenawarenessoptions23) | No | On-screen awareness parameter list. If not passed, the default parameter configuration is used. |
| callback | Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)[]&gt; | Yes | Callback function used to return the screen awareness result. The returned awareness information list **OnscreenAwarenessInfo[]** returns at most two awareness information items at a time. |

**Error Code**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**Example**

   ```ts
   import { onScreen } from '@kit.MultimodalAwarenessKit';
   let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
      groupId: 'SmartEdge',
   }

   let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
      parameters: {
         "SmartEdge" : {
            "windowId":'102',
         }
      }
   }
   try {
      onScreen.subscribe(onscreenAwarenessCap, (info: onScreen.OnscreenAwarenessInfo[]) => {
         console.info(`subscribe resultCode: ${info[0].resultCode}`);
      }, onscreenAwarenessOptions);
   } catch (err) {
      console.error(`subscribe failed, Code: ${err.code}, message: ${err.message}`);
   }
   ```

## onScreen.unsubscribe<sup>23+</sup>

unsubscribe(capability: OnscreenAwarenessCap, callback?: Callback&lt;OnscreenAwarenessInfo[]&gt;): void

Disables proactive on-screen content awareness and unsubscribes from the on-screen awareness result.

**Required permissions:**

- API version 26+: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS.
- API version 23-24: ohos.permission.GET_SCREEN_CONTENT.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                             | Mandatory | Description               |
| -------- | -------------------------------- | ---- | ---------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes   | On-Screen Awareness capability list. |
| callback | Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)[]&gt; | No   | Callback to be unsubscribed. If omitted, all callbacks of this awareness capability are removed. The returned awareness information list OnscreenAwarenessInfo[] returns at most 2 awareness information items at a time.|

**Error Codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: **ohos.permission.GET_SCREEN_CONTENT** or **ohos.permission.ONSCREEN_AWARENESS**. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
   groupId: 'SmartEdge'
}

try {
  onScreen.unsubscribe(onscreenAwarenessCap, (info: onScreen.OnscreenAwarenessInfo[]) => {
    console.info(`unsubscribe resultCode: ${info[0].resultCode}`);
  });
} catch (err) {
  console.error(`unsubscribe failed, Code: ${err.code}, message: ${err.message}`);
}
```

## onScreen.trigger<sup>23+</sup>

trigger(capability: OnscreenAwarenessCap, options?: OnscreenAwarenessOptions): Promise&lt;OnscreenAwarenessInfo&gt;

Actively triggers on-screen content awareness to obtain the current on-screen awareness result.

**Required Permission:**

- API version 26+: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS.
- API versions 23-24: ohos.permission.GET_SCREEN_CONTENT.

**System Capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                             | Mandatory | Description                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes   | On-screen awareness capability list. For the supported list, see [OnscreenAwarenessCap](#onscreenawarenesscap23). |
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| No   | On-screen awareness parameter list. If not passed, the default parameter configuration is used.|

**Returns**

  | Type                           | Description         |
  | ---------------------------- | ---------- |
  | Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | Promise object used to return the screen awareness result. |

**Error Code**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'UiImage'
  ]
}

let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
  parameters: {
    "windowId": 102
  } as Record<string, Object>
}
try {
  let info: onScreen.OnscreenAwarenessInfo =
    await onScreen.trigger(onscreenAwarenessCap, onscreenAwarenessOptions);
  console.info(`trigger resultCode: ${info.resultCode}`);
} catch (err) {
  console.error(`trigger failed, Code: ${err.code}, message: ${err.message}`);
}
```

## onScreen.capture<sup>23+</sup>

capture(capability: OnscreenAwarenessCap, options?: OnscreenAwarenessOptions): Promise&lt;OnscreenAwarenessInfo[]&gt;

Actively triggers on-screen content awareness to obtain page information.

**Required Permission**

- API version 26+: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS.
- API version 23-24: ohos.permission.GET_SCREEN_CONTENT.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device Behavior Differences** This API works normally only on Phone, Tablet, and Car devices (on Car devices, capList must be UiTree). Calling it on other device types returns error code 801.

**System API** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                             | Mandatory | Description                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes   | On-screen awareness capability list. For details, see the supported capability list below.|
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| No   | On-screen awareness parameter list. If not passed, the default parameter configuration is used.|

The capList capability list supported by the capture API is as follows:
|capList Capability List|Description|
| ---- | ------ |
|UiImage|Obtains the sub-image information in the page.|
|QuickSnap|Obtains the screenshot information.|
|UiTree|Obtains the page JSON tree information.<br> **Since:** 26.0.0|

**Returns**

  | Type                           | Description         |
  | ---------------------------- | ---------- |
  | Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)[]&gt; | Promise object used to return the on-screen awareness result. The returned awareness information list OnscreenAwarenessInfo[] contains at most two awareness information items at a time.|

**Error codes:**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**UiImage Example:**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'UiImage',
  ]
}
try {
  let info: onScreen.OnscreenAwarenessInfo[] = await onScreen.capture(onscreenAwarenessCap);
  console.info(`capture resultCode: ${info[0].resultCode}`);
} catch (err) {
  console.error(`capture failed, Code: ${err.code}, message: ${err.message}`);
}
```

**UiTree Example:**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'UiTree',
  ]
}
try {
  let info: onScreen.OnscreenAwarenessInfo[] = await onScreen.capture(onscreenAwarenessCap);
  console.info(`capture resultCode: ${info[0].resultCode}`);
} catch (err) {
  console.error(`capture failed, Code: ${err.code}, message: ${err.message}`);
}
```
## onScreen.interact<sup>23+</sup>

interact(capability: OnscreenAwarenessCap, options?: OnscreenAwarenessOptions): Promise&lt;OnscreenAwarenessInfo[]&gt;

Actively triggers on-screen behavior interaction to recognize interface behaviors and provide behavior feedback. For example, when the capList Capability List is JumpContext, a tap precisely jumps to the specified paragraph and highlights the text through the feedback information. When the capList Capability List is InjectEvent, a tap executes the corresponding click event.

**Required Permission**

- API version 26+: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS.
- API version 23-24: ohos.permission.GET_SCREEN_CONTENT.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device Behavior Differences**: This API only supports Phone, Tablet, and Car devices (on Car devices, capList must be InjectEvent). Calling it on other device types returns error code 801.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                             | Mandatory | Description                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes   | On-screen awareness capability list. For details, see the supported capability list below.|
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| No   | On-screen awareness parameter list. If not passed, the default parameter configuration is used.|

The capList capability list supported by the interact API is as follows:
|capList Capability List|Description|
| ---- | ------ |
|JumpContext|Highlights and jumps to the specified context.|
|InjectEvent|Injects an event. When the capList capability list is **InjectEvent**, the options field is mandatory, and its content must comply with the **InjectEvent** option specification (see the example for details). If options does not comply with the specification, the injection operation fails and error code 34000001 is returned.<br> **Since:** 26.0.0|
|SmartAutoFill|Intelligently fills in the page input box content. When the capList capability list is **SmartAutoFill**, options must contain the **autoFillItems** array (see the example for details); otherwise, the fill operation fails and error code 34000001 is returned.<br> **Since:** 26.0.0|

**Returns**

  | Type                           | Description         |
  | ---------------------------- | ---------- |
  | Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)[]&gt; | Promise object used to return the on-screen awareness result. The returned awareness information list OnscreenAwarenessInfo[] returns at most two awareness information items at a time.|

**Error Codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**JumpContext Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'JumpContext',
  ]
}

let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
  parameters: {
    "JumpContext" : {
      "pageId":'156',
      "textCompIdList": ['235'],
      "text": 'Beginning of the article'
    }
  }
}

try {
  let info: onScreen.OnscreenAwarenessInfo[] = await onScreen.interact(onscreenAwarenessCap, onscreenAwarenessOptions);
  console.info(`interact resultCode: ${info[0].resultCode}`);
} catch (err) {
  console.error(`interact failed, Code: ${err.code}, message: ${err.message}`);
}
```

**InjectEvent Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'InjectEvent',    // (Mandatory field) Inject event capability: indicates that the current service needs to use event injection (such as system event injection for key presses, clicks, and back operations).
  ]
}

let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
  parameters: {
     // (Required field) Command for injecting an event, used to inject key/operation events into the system.
    "InjectEvent": {
       // (injectEvent is required, others are optional) Specific content of the injected event: JSON string format, including the component type, action to execute, and parameters.
      "injectEvent": '{"componentType":"","action":"back","params":{}}',
      "compId": ["0"],    // (Optional) Target component ID array: specifies the IDs of the components into which the event is injected.
      "windowId": 0,      // (Optional) Window ID: specifies the target window for the injected event. 0 indicates the currently active window.
      "displayId": -1     // (Optional) Display device ID: -1 indicates using the default display device.
    }
  }
}

try {
  let info: onScreen.OnscreenAwarenessInfo[] = await onScreen.interact(onscreenAwarenessCap, onscreenAwarenessOptions);
  console.info(`interact resultCode: ${info[0].resultCode}`);
} catch (err) {
  console.error(`interact failed, Code: ${err.code}, message: ${err.message}`);
}
```
**SmartAutoFill Example**

When **capList** is **SmartAutoFill**, options must be passed and the **"SmartAutoFill"** object in parameters must contain the **autoFillItems** array; otherwise, the fill operation fails and error code 34000001 is returned. The fields of each element in the **autoFillItems** array are described as follows:

| Field Name | Type | Mandatory | Description |
| ---- | ------ | ---- | ---- |
| frameworkType | number | No | UI framework type. **0**: **ARKUI** (default); **1**: **ARKWEB**. |
| id | string | Yes | Input box component ID. When **frameworkType** is **0** (**ARKUI**), id is the component ID in numeric string form; when **frameworkType** is **1** (**ARKWEB**), id is the Web component ID. |
| xpath | string | No | XPath path. Required when **frameworkType** is 1 (**ARKWEB**), used to locate the input box element in the Web page. |
| contentType | string | No | Content type of the input box. |
| clickPoints | object[] | No | List of click coordinates, used to specify the click position of the input box. |
| existingValue | string | No | Content already existing in the input box. |
| fillValue | string | No | Content to be filled. If not passed, the fill content is an empty string. |
| mode | number | No | Fill mode. **0**: overwrite the existing content (**OVERWRITE**, default); **1**: insert content (**INSERT**). |

The fields of each element in the **clickPoints** array are described as follows:

| Field Name | Type | Mandatory | Description |
| ---- | ------ | ---- | ---- |
| displayX | number | No | X coordinate of the click position (absolute screen coordinate). |
| displayY | number | No | Y coordinate of the click position (absolute screen coordinate). |

The **autoFillItems** array supports a maximum of 50 elements.

The **SmartAutoFill** object can also contain the following optional fields, which are used to specify the target window information for filling:

| Field Name | Type | Mandatory | Description |
| ---- | ------ | ---- | ---- |
| pageInfo | object | No | Page information, used to specify the target window for filling. |

The fields in the **pageInfo** object are described as follows:

| Field Name | Type | Mandatory | Description |
| ---- | ------ | ---- | ---- |
| bundleName | string | No | Application package name. |
| displayId | number | No | Display device ID. |
| windowId | number | No | Window ID, which specifies the target window for filling. If this parameter is not passed or an invalid value (≤ 0) is passed, the system automatically obtains the main window ID of the current foreground application. |

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';

let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  capList: [
    'SmartAutoFill',
  ]
};

let onscreenAwarenessOptions: onScreen.OnscreenAwarenessOptions = {
  parameters: {
    "SmartAutoFill": {
      autoFillItems: [
        {
          frameworkType: 0,
          id: "123",
          contentType: "EMAIL_ADDRESS",
          fillValue: "user@example.com",
          mode: 0
        },
        {
          frameworkType: 1,
          id: "456",
          xpath: "/html/body/div/form/input[1]",
          contentType: "PHONE_NUMBER",
          fillValue: "13800138000",
          mode: 0
        }
      ],
      pageInfo: {
        windowId: 10
      }
    }
  }
};

try {
  let info: onScreen.OnscreenAwarenessInfo[] = await onScreen.interact(onscreenAwarenessCap, onscreenAwarenessOptions);
  console.info(`interact resultCode: ${info[0].resultCode}`);
} catch (err) {
  console.error(`interact failed, Code: ${err.code}, message: ${err.message}`);
}
```
## onScreen.apperceive<sup>23+</sup>

apperceive(capability: OnscreenAwarenessCap, options?: OnscreenAwarenessOptions): Promise&lt;OnscreenAwarenessInfo[]&gt;

Actively triggers on-screen content awareness to obtain the screen content for snapshot analysis.

**Required permission:**

- API version 26+: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS.
- API version 23-24: ohos.permission.GET_SCREEN_CONTENT.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                             | Mandatory | Description                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | Yes   | On-screen awareness capability list. For details, see the supported capability list below.|
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| No   | On-screen awareness parameter list. If this parameter is not passed, the default parameter configuration is used.|

The groupId capability list supported by the apperceive API is as follows:
|groupId Capability List|Corresponding Sub-Item Capability|Description|
| ---- | ------ | ------|
|SmartEdge|Article|Obtains the reading scenario awareness information.|
|SmartEdge|ShortVideo|Obtains the short video scenario awareness information.|
|SmartEdge|Todo|Obtains the to-do scenario awareness information.|
|SmartEdge|Activity|Obtains the basic service awareness information.|
|CeliaMemory|Article|Obtains the reading scenario awareness information.|

**Returns**

  | Type                           | Description         |
  | ---------------------------- | ---------- |
  | Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)[]&gt; | Promise object used to return the on-screen awareness result. The returned awareness information list OnscreenAwarenessInfo[] contains at most two awareness information items at a time.|

**Error Codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
let onscreenAwarenessCap: onScreen.OnscreenAwarenessCap = {
  groupId: 'SmartEdge'
}
try {
  let info: onScreen.OnscreenAwarenessInfo[] = await onScreen.apperceive(onscreenAwarenessCap);
  console.info(`apperceive resultCode: ${info[0].resultCode}`);
} catch (err) {
  console.error(`apperceive failed, Code: ${err.code}, message: ${err.message}`);
}
```

## onScreen.onReadingScreenPermissionListener<sup>23+</sup>

onReadingScreenPermissionListener(callback: Callback&lt;ReadingScreenPermissionStatus&gt;): void

Enables monitoring of the screen content access permission and returns the permission status in real time.

**Required permission:** ohos.permission.GET_SCREEN_CONTENT

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| callback | Callback&lt;[ReadingScreenPermissionStatus](#readingscreenpermissionstatus23)&gt; | Yes | Callback invoked to return the permission status of reading screen information. |

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
try {
   onScreen.onReadingScreenPermissionListener((info: onScreen.ReadingScreenPermissionStatus) => {
      console.info(`onReadingScreenPermissionListener succeeded, readingState: ${info.readingState}`);
   });
} catch (err) {
   console.error(`onReadingScreenPermissionListener failed, Code: ${err.code}, message: ${err.message}`);
}
```

## onScreen.offReadingScreenPermissionListener<sup>23+</sup>

offReadingScreenPermissionListener(callback?: Callback&lt;ReadingScreenPermissionStatus&gt;): void

Closes the monitoring of screen content access permission.

**Required permission:** ohos.permission.GET_SCREEN_CONTENT

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**Device behavior differences:** This API can be properly called on Phone and Tablet devices. If it is called on other device types, error code 801 is returned.

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;[ReadingScreenPermissionStatus](#readingscreenpermissionstatus23)&gt; | No | Callback for the screen content access permission event. The callback to be unsubscribed from must be the same as the one passed in during subscription. If this parameter is not specified, all callbacks currently listening for this event are unsubscribed from. |

**Error codes**

For details about the error codes, see [Onscreen Awareness Error Codes](errorcode-onScreen.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**Example**

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
try {
  onScreen.offReadingScreenPermissionListener();
  console.info(`offReadingScreenPermissionListener succeeded.`);
} catch (err) {
  console.error(`offReadingScreenPermissionListener failed, Code: ${err.code}, message: ${err.message}`);
}
```
