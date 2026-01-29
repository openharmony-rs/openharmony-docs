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

## onScreen.Scenario

定义屏上内容的场景类型。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| UNKNOWN | 0    | 表示屏上内容所处场景未知。 |
| ARTICLE | 1    | 表示屏上内容处于文章场景。 |

## onScreen.EventType

定义控制事件的类型。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| SCROLL_TO_HOOK  | 1    | 表示滚动到hook点事件。 |

## onScreen.Paragraph

段落信息。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| hookId   | number | 否   | 是   | 段落对应的hook ID，每个主要段落的标识。 |
| chapterId   | number | 否   | 是   | 段落对应的chapter ID，每个子章节的标识。 |
| title    | string | 否   | 是   | 段落对应的标题。 |
| text    | string | 否   | 是   | 段落对应的内容。 |

## onScreen.ContentOptions

屏上内容的获取选项。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | 否   | 是   | 需要获取内容的窗口ID，不赋值或赋值undefined则默认获取全屏窗口。 |
| contentUnderstand   | boolean | 否   | 是   | 是否需要进行内容理解，默认为否。 |
| pageLink    | boolean | 否   | 是   | 是否获取复访链接，默认为否。 |
| textOnly    | boolean | 否   | 是   | 是否只获取文本并划分段落，默认为否。 |

## onScreen.PageContent

屏上内容。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | 否   | 否   | 获取到的屏上内容的窗口ID |
| sessionId   | number | 否   | 否   | 此次调用该接口的session ID，标识当次调用动作。 |
| bundleName    | string | 否   | 否   | 获取到的屏上内容的包名。 |
| scenario    | [Scenario](#onscreenscenario) | 否   | 是   | 获取到的屏上内容的场景。只有在options.contentUnderstand为true时，才会获取该属性。 |
| title    | string | 否   | 是   | 获取到的屏上内容的标题。只有在options.contentUnderstand为true时，才会获取该属性。 |
| content    | string | 否   | 是   | 获取到的屏上内容的正文。只有在options.contentUnderstand为true时，才会获取该属性。 |
| pageLink    | string | 否   | 是   | 获取到的屏上内容的复访链接。只有在options.pageLink为true时，才会获取该属性。 |
| paragraphs    | [Paragraph](#onscreenparagraph)[] | 否   | 是   | 获取到的文本段落信息。只有在options.textOnly为true时，才会获取该属性。 |

## onScreen.ControlEvent

控制事件。

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

| 名称 | 类型   | 只读 | 可选 | 说明                                     |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| windowId   | number | 否   | 否   | 控制事件要操作的窗口的window ID。 |
| sessionId   | number | 否   | 否   | 控制事件要操作的session ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](#onscreenpagecontent)提供。 |
| eventType    | [EventType](#onscreeneventtype) | 否   | 否   | 控制事件类型。 |
| hookId    | number | 否   | 是   | 控制事件对应的hook ID。控制事件要操作的hook ID和该次会话对应的session ID都由某次会话获取的[PageContent](#onscreenpagecontent)提供。 |

## onScreen.getPageContent

getPageContent(options?: [ContentOptions](#onscreencontentoptions)): Promise&lt;[PageContent](#onscreenpagecontent)&gt;

在需要抓取内容的窗口在桌面上时，调用该接口以获取屏上内容。

**需要权限**：ohos.permission.GET_SCREEN_CONTENT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| options | [ContentOptions](#onscreencontentoptions)   | 否   | 获取屏上内容的选项，默认为不指定window ID，且其余选项均为false。 |

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

sendControlEvent(event: [ControlEvent](#onscreencontrolevent)): Promise&lt;void&gt;

在需要控制的窗口在桌面上时，在调用[onScreen.getPageContent](#onscreengetpagecontent)后，根据其返回的段落信息，调用该接口发送屏上控制事件。

**需要权限**：ohos.permission.SIMULATE_USER_INPUT.

**系统能力**：SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统API**：此接口为系统接口

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------- |
| event | [ControlEvent](#onscreencontrolevent)   | 是   | 屏上控制事件。 |

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