# sendControlEvent（系统接口）

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## sendControlEvent

```TypeScript
function sendControlEvent(event: ControlEvent): Promise<void>
```

在需要控制的窗口在桌面上时，在调用[onScreen.getPageContent](arkts-multimodalawareness-onscreen-getpagecontent-f-sys.md)后，根据其返回的段落信息，调用该接口发送屏上控制事件。

**起始版本：** 20

**需要权限：** ohos.permission.SIMULATE_USER_INPUT

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ControlEvent](arkts-multimodalawareness-onscreen-controlevent-i-sys.md) | 是 | 屏上控制事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.SIMULATE_USER_INPUT. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [34000005](../errorcode-onScreen.md#34000005-目标未找到) | The target is not found. |

**示例**

```TypeScript
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
