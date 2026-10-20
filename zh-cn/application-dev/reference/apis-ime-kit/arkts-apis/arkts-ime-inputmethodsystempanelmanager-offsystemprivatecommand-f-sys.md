# offSystemPrivateCommand（系统接口）

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## offSystemPrivateCommand

```TypeScript
function offSystemPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void
```

取消订阅系统预置输入法应用发送私有数据命令的事件。<br> <br>使用场景：当系统面板不再需要接收来自输入法应用的私有命令通知时使用此接口，如面板关闭或退出时。<br> <br>相关接口间的配合/制约关系：取消订阅后，之前通过onSystemPrivateCommand注册的回调将不再被触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function offSystemPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void--><!--Device-inputMethodSystemPanelManager-function offSystemPrivateCommand(callback?: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt;&gt; | 否 | 回调函数。<br>使用场景：传入需要取消的特定回调函数时，仅取消该回调的订阅。<br>默认值：不传入时，取消所有已订阅的onSystemPrivateCommand回调。<br>说明：建议传入需要取消的特定回调函数引用，避免取消所有回调导致其他订阅者的回调也被移除。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
