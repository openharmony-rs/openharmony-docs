# trigger（系统接口）

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## trigger

```TypeScript
function trigger(capability: OnscreenAwarenessCap, 
                   options?: OnscreenAwarenessOptions): Promise<OnscreenAwarenessInfo>
```

主动触发屏幕内容感知，获取当前屏幕感知结果。

**起始版本：** 23

**需要权限：** 
- API版本26.0.0+：ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS
- API版本23 - 24：ohos.permission.GET_SCREEN_CONTENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-onScreen-function trigger(capability: OnscreenAwarenessCap,                    options?: OnscreenAwarenessOptions): Promise<OnscreenAwarenessInfo>--><!--Device-onScreen-function trigger(capability: OnscreenAwarenessCap,                    options?: OnscreenAwarenessOptions): Promise<OnscreenAwarenessInfo>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md) | 是 | 屏上感知能力列表，支持列表见 [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md)。 |
| options | [OnscreenAwarenessOptions](arkts-multimodalawareness-onscreen-onscreenawarenessoptions-i-sys.md) | 否 | 屏上感知参数列表，不传递则使用默认参数配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OnscreenAwarenessInfo](arkts-multimodalawareness-onscreen-onscreenawarenessinfo-i-sys.md)&gt; | Promise对象，返回屏幕感知结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited <br> device capabilities. |
| [34000002](../../apis-multimodalawareness-kit/errorcode-carAwareness.md#34000002-指定能力不支持) | The application or page is not supported. |
| [34000001](../../apis-multimodalawareness-kit/errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get page content forbidden by <br> permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |

**示例**

```TypeScript
import onScreen from "@ohos.multimodalAwareness.onScreen";
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

