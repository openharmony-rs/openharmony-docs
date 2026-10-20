# onDisconnectWithInfo（系统接口）

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## onDisconnectWithInfo

```TypeScript
function onDisconnectWithInfo(callback: Callback<ScreenDisconnectInfo>): void
```

开启屏幕断连事件的监听。屏幕断连时，调用回调函数返回断连信息。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-screen-function onDisconnectWithInfo(callback: Callback<ScreenDisconnectInfo>): void--><!--Device-screen-function onDisconnectWithInfo(callback: Callback<ScreenDisconnectInfo>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ScreenDisconnectInfo](arkts-arkui-screen-screendisconnectinfo-i-sys.md)&gt; | 是 | 回调函数。返回屏幕断连信息，包含屏幕id和断连原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
