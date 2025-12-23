# @ohos.multimodalAwareness.onScreen（屏上感知）(系统接口)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供对屏上内容的感知能力。

> **说明：**
>
> 1. 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 2. 本模块为系统接口。

## 导入模块

```ts
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## Scenario

定义屏上内容的场景类型。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| UNKNOWN | 0    | 表示屏上内容所处场景未知。 |
| ARTICLE | 1    | 表示屏上内容处于文章场景。 |

## EventType

定义控制事件的类型。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| SCROLL_TO_HOOK  | 1    | 表示滚动到hook点事件。 |

## Paragraph

段落信息。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| hookId   | number | 否   | 是   | 段落对应的hook ID，每个主要段落的标识。 |
| chapterId   | number | 否   | 是   | 段落对应的chapter ID，每个子章节的标识。 |
| title    | string | 否   | 是   | 段落对应的标题。 |
| text    | string | 否   | 是   | 段落对应的内容。 |

## ContentOptions

屏上内容的获取选项。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | 否   | 是   | 需要获取内容的窗口ID，不赋值或赋值undefined则默认获取全屏窗口。 |
| contentUnderstand   | boolean | 否   | 是   | 是否需要进行内容理解，默认为否。 |
| pageLink    | boolean | 否   | 是   | 是否获取复访链接，默认为否。 |
| textOnly    | boolean | 否   | 是   | 是否只获取文本并划分段落，默认为否。 |

## PageContent

屏上内容。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | 否   | 否   | 获取到的屏上内容的窗口ID |
| sessionId   | number | 否   | 否   | 此次调用该接口的session ID，标识当次调用动作。 |
| bundleName    | string | 否   | 否   | 获取到的屏上内容的包名。 |
| scenario    | [Scenario](#scenario) | 否   | 是   | 获取到的屏上内容的场景。只有在options.contentUnderstand为true时，才会获取该属性。 |
| title    | string | 否   | 是   | 获取到的屏上内容的标题。只有在options.contentUnderstand为true时，才会获取该属性。 |
| content    | string | 否   | 是   | 获取到的屏上内容的正文。只有在options.contentUnderstand为true时，才会获取该属性。 |
| pageLink    | string | 否   | 是   | 获取到的屏上内容的复访链接。只有在options.pageLink为true时，才会获取该属性。 |
| paragraphs    | [Paragraph](#paragraph)[] | 否   | 是   | 获取到的文本段落信息。只有在options.textOnly为true时，才会获取该属性。 |

## ControlEvent

控制事件。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | 否   | 否   | 控制事件要操作的窗口的window ID。 |
| sessionId   | number | 否   | 否   | 控制事件要操作的session ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](#pagecontent)提供。 |
| eventType    | [EventType](#eventtype) | 否   | 否   | 控制事件类型。 |
| hookId    | number | 否   | 是   | 控制事件对应的hook ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](#pagecontent)提供。 |

## OnscreenAwarenessCap<sup>23+</sup>

屏上感知能力（包括阅读场景感知、OCR识别等功能）。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| capList   | string[] | 否   | 否   | 表示能力列表, 包含页面内容、页面链接、文本选择等能力。  |

|能力列表|功能说明|
| ---- | ------ |
|contentUiTree|获取控件树信息|
|contentUiOcr|获取OCR识别信息|
|contentScreenshot|获取截屏信息|
|contentLink|获取页面复访链接|
|contentUiTreeWithImage|获取控件树和控件内图片信息|
|interactionTextSelection|获取文本选择信息|
|interactionClick|获取点击事件，以及控件节点信息|
|interactionScroll|获取滚动事件，以及控件节点信息|
|scenarioReading|获取阅读场景感知信息|
|scenarioShortVideo|获取短视频场景的感知信息|
|scenarioTodo|获取待办场景的感知信息|

## OnscreenAwarenessOptions<sup>23+</sup>

屏上感知参数列表，用于特定场景下获取屏上信息，如提供窗口ID用以采集应用界面内容和链接。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| parameters   | Record<string, Object> | 否   | 是   | 感知参数列表，参数结果是key-value数据对象。 |

## CollectStrategy<sup>23+</sup>

页面信息收集策略。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| ALLOW | 1 << 0    | 应用支持采集 |
| SPLIT_SCREEN | 1 << 1    | 应用分屏窗口采集策略。 |
| UNSUPPORTED_APP | 1 << 2  | 应用不支持。 |
| PRIVATE_WINDOW | 1 << 3  | 应用隐私窗口。 |
| VM_APP | 1 << 4 | 虚拟机应用，非鸿蒙应用。 |

## EntityInfo<sup>23+</sup>

提供感知到的实体信息，包括内容、链接、图像和其他类型的实体。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| entityName   | string | 否   | 否   | 感知结果实体名称，固定内容。 |
| entityInfo   | Record<string, Object> | 否   | 否   | 感知结果实体信息，包括内容、链接、图像和其他实体。|


## OnscreenAwarenessInfo<sup>23+</sup>

屏上感知返回信息列表。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| resultCode  | number | 否   | 否   | 返回码，默认0 表示成功。 |
| timestamp   | number | 否   | 否   | 表示进入特定页面的时间戳。 |
| bundleName  | string | 否   | 是   | 应用包名。 |
| appID      | string | 否   | 是   | 小程序ID，如微信、支付宝等三方应用小程序ID。 |
| appIndex   | number | 否   | 是   | 应用索引。 |
| pageId     | string | 否   | 是   | 应用页面ID。 |
| sampleId   | string | 否   | 是   | 采集记录ID。 |
| collectStrategy   | number | 否   | 是   | 页面采集策略，是 [CollectStrategy](#collectstrategy23) 的按位或运算组合。 |
| displayId   | number | 否   | 是   | 屏幕ID。 |
| windowId    | number | 否   | 是   | 窗口ID。 |
| entityInfo  | [EntityInfo](#entityinfo23)[] | 否   | 是   | 实体信息。|

## onScreen.getPageContent

getPageContent(options?: [ContentOptions](#contentoptions)): Promise&lt;[PageContent](#pagecontent)&gt;

在需要抓取内容的窗口在桌面上时，调用该接口以获取屏上内容。

**需要权限**：ohos.permission.GET_SCREEN_CONTENT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| options | [ContentOptions](#contentoptions)   | 否   | 获取屏上内容的选项，默认为不指定window ID，且其余选项均为false。 |

**错误码**：

以下错误码的详细介绍请参见[屏上感知错误码](errorcode-onScreen.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |
| 34000003 | The window ID is invalid. Possible causes: 1. window id is not passed when screen is splited. 2. passed window id is not on screen or floating. |
| 34000004 | The page is not ready. |
| 34000006 | The request timed out. |

**示例**：

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

在需要控制的窗口在桌面上时，在调用[onScreen.getPageContent](#onscreengetpagecontent)后，根据其返回的段落信息，调用该接口发送屏上控制事件。

**需要权限**：ohos.permission.SIMULATE_USER_INPUT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| event | [ControlEvent](#controlevent)   | 是   | 屏上控制事件。 |

**错误码**：

以下错误码的详细介绍请参见[屏上感知错误码](errorcode-onScreen.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.SIMULATE_USER_INPUT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000005 | The target is not found. |

**示例**：

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
subscribe(capability: [OnscreenAwarenessCap](#onscreenawarenesscap23), 
          callback: Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt;, 
          options?: [OnscreenAwarenessOptions](#onscreenawarenessoptions23)): void

开启屏幕内容主动感知，并订阅屏幕感知结果。

**需要权限**：ohos.permission.GET_SCREEN_CONTENT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**设备行为差异**：该接口在Phone和Tablet中可正常调用，在其他设备类型中返回801错误码。

**系统API**：此接口为系统接口

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | 是   | 屏上感知能力列表。 |
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| 否   | 屏上感知参数列表。|
| callback | Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | 是   | 回调函数，返回屏幕感知结果。|


**错误码**：

以下错误码的详细介绍请参见[屏上感知错误码](errorcode-onScreen.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**示例**：

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

unsubscribe(capability: [OnscreenAwarenessCap](#onscreenawarenesscap23), 
            callback?: Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt;): void

关闭屏幕内容主动感知，并取消订阅屏幕感知结果。

**需要权限**：ohos.permission.GET_SCREEN_CONTENT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**设备行为差异**：该接口在Phone和Tablet中可正常调用，在其他设备类型中返回801错误码。

**参数**：

| 参数名   | 类型                             | 必填 | 说明               |
| -------- | -------------------------------- | ---- | ---------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | 是   | 屏上感知能力列表。 |
| callback | Callback&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | 是   | 回调函数，返回屏幕感知结果。|

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |

**示例**：

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

trigger(capability: [OnscreenAwarenessCap](#onscreenawarenesscap23), 
        options?: [OnscreenAwarenessOptions](#onscreenawarenessoptions23)): Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt;

主动触发屏幕内容感知，获取当前屏幕感知结果。

**需要权限**：ohos.permission.GET_SCREEN_CONTENT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**设备行为差异**：该接口在Phone和Tablet中可正常调用，在其他设备类型中返回801错误码。

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| capability | [OnscreenAwarenessCap](#onscreenawarenesscap23)   | 是   | 屏上感知能力列表。 |
| options|[OnscreenAwarenessOptions](#onscreenawarenessoptions23)| 否   | 屏上感知参数列表。|


**返回值：**

  | 类型                           | 说明         |
  | ---------------------------- | ---------- |
  | Promise&lt;[OnscreenAwarenessInfo](#onscreenawarenessinfo23)&gt; | Promise对象，返回屏幕感知结果。 |
**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT. |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities.|
| 34000001 | Service exception. |
| 34000002 | The application or page is not supported. |

**示例**：

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