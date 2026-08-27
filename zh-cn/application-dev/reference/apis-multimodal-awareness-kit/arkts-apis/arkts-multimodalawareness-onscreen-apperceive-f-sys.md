# apperceive（系统接口）

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## apperceive

```TypeScript
function apperceive(capability: OnscreenAwarenessCap, 
                   options?: OnscreenAwarenessOptions): Promise<OnscreenAwarenessInfo[]>
```

主动触发屏幕内容感知，获取屏幕内容进行快照分析。

**起始版本：** 23

**需要权限：** 
- API版本26.0.0+：ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS
- API版本23 - 24：ohos.permission.GET_SCREEN_CONTENT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md) | 是 | 屏上感知能力列表，具体见下面支持的能力列表。 |
| options | [OnscreenAwarenessOptions](arkts-multimodalawareness-onscreen-onscreenawarenessoptions-i-sys.md) | 否 | 屏上感知参数列表，不传此参数时，使用默认参数配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OnscreenAwarenessInfo](arkts-multimodalawareness-onscreen-onscreenawarenessinfo-i-sys.md)[]&gt; | Promise对象，返回屏幕感知结果。返回的感知信息列表 OnscreenAwarenessInfo[] 最多同时返回2个感知信息项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. An attempt was made to get page content forbidden by permission: ohos.permission.GET_SCREEN_CONTENT or ohos.permission.ONSCREEN_AWARENESS. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Function can not work correctly due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-服务异常) | Service exception. |
| [34000002](../errorcode-carAwareness.md#34000002-指定能力不支持) | The application or page is not supported. |

**示例**

```TypeScript
import onScreen from "@ohos.multimodalAwareness.onScreen";
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
