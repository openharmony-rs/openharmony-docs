# onSystemPrivateCommand（系统接口）

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## onSystemPrivateCommand

```TypeScript
function onSystemPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void
```

订阅系统预置输入法应用发送私有数据命令的事件。当输入法应用通过inputMethodEngine.sendPrivateCommand（TextInputClient方法）向系统组件发送私有命令时，系统面板会通过此回调接收到该命令数据。<br> <br>使用场景：当系统面板需要接收来自输入法应用的私有数据命令（如自定义配置、状态通知等）时使用此接口。<br> <br>使用后效果：订阅成功后，每当输入法应用发送私有命令，系统面板将通过callback接收到Record<string, CommandDataType>格式的命令数据。<br> <br>前提条件：需先调用connectSystemChannel建立系统通道连接。<br> <br>相关接口间的配合/制约关系：本接口是系统面板侧的私有命令接收接口，对应输入法应用侧的inputMethodEngine.sendPrivateCommand（发送端）和inputMethodEngine.on('privateCommand')（输入法应用侧接收端）。私有命令通信方向：输入法应用 → 系统面板。<br> <br> | 参数名 | 类型 | 必填 | 说明 |

| -------- | -------- | -------- | -------- |  
| callback | Callback&lt;Record&lt;string, CommandDataType&gt;&gt;| 是 | 回调函数，当输入法应用发送私有数据命令时触发。<br>使用场景：必须提供此回调函数以处理输入法应用发送的私有命令数据。<br>使用后效果：回调触发时，参数为Record<string, CommandDataType>格式，其中key为命令名称，value为命令数据值（支持number、string、boolean类型）。<br>说明：回调中的数据格式为键值对映射，开发者需根据key值判断命令类型并执行相应逻辑。 |

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function onSystemPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void--><!--Device-inputMethodSystemPanelManager-function onSystemPrivateCommand(callback: Callback<Record<string, CommandDataType>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt;&gt; | 是 | 当输入法应用发送私有数据命令时触发的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
