# subscribe（系统接口）

## subscribe

```TypeScript
function subscribe(capability: OnscreenAwarenessCap,
                     callback: Callback<OnscreenAwarenessInfo[]>, 
                     options?: OnscreenAwarenessOptions): void
```

开启屏幕内容主动感知，并订阅屏幕感知结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本26.0.0+：ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS
- API版本23 - 24：ohos.permission.GET_SCREEN_CONTENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-onScreen-function subscribe(capability: OnscreenAwarenessCap,                     callback: Callback<OnscreenAwarenessInfo[]>,                      options?: OnscreenAwarenessOptions): void--><!--Device-onScreen-function subscribe(capability: OnscreenAwarenessCap,                     callback: Callback<OnscreenAwarenessInfo[]>,                      options?: OnscreenAwarenessOptions): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md) | 是 | 屏上感知能力列表。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[OnscreenAwarenessInfo](arkts-multimodalawareness-onscreen-onscreenawarenessinfo-i-sys.md)[]&gt; | 是 | 回调函数，返回屏幕感知结果。返回的感知信息列表 OnscreenAwarenessInfo[] 最多同时返回2个感知信 息项。 |
| options | [OnscreenAwarenessOptions](arkts-multimodalawareness-onscreen-onscreenawarenessoptions-i-sys.md) | 否 | 屏上感知参数列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited &lt;br&gt; device capabilities. |
| [34000002](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000002-应用或页面不支持) | The application or page is not supported. |
| [34000001](../../apis-multimodalawareness-kit/errorcode-onScreen.md#34000001-服务异常) | Service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get page content forbidden by &lt;br&gt; permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |

## 示例

```TypeScript
import onScreen from "@ohos.multimodalAwareness.onScreen";
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
   console.error('subscribe failed, errCode = ' + err.code);
}
```

