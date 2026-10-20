# sendPrivateCommand（系统接口）

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## sendPrivateCommand

```TypeScript
function sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>
```

发送私有命令给系统预置输入法应用。使用Promise异步回调。<br> <br>含义/功能：系统面板向系统预置输入法应用发送自定义私有数据命令，数据格式为键值对映射（Record<string, CommandDataType>）。<br> <br>使用场景：当系统面板需要向输入法应用发送自定义配置命令、状态通知等私有数据时使用此接口。私有数据通道是系统预置输入法应用与系统特定组件的通信机制，常用于设备级厂商在特定设备上实现自定义的输入法功能。<br> <br>使用后效果：调用后，私有命令数据将发送给当前系统预置输入法应用。输入法应用可通过inputMethodEngine.on('privateCommand')接收此命令数据。<br> <br>前提条件：需先调用connectSystemChannel建立系统通道连接。<br> <br>相关接口间的配合/制约关系：本接口是系统面板侧的私有命令发送接口，对应输入法应用侧的inputMethodEngine.on('privateCommand')（接收端）。私有命令通信方向：系统面板 → 输入法应用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>--><!--Device-inputMethodSystemPanelManager-function sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commandData | Record&lt;string, [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md)&gt; | 是 | 要发送的命令数据，格式为键值对映射，key为命令名称（string类型），value为命令数据值（支持number、string或boolean类型）。<br>使用场景：用于传输系统面板与输入法应用之间的自定义通信数据。<br>取值范围：总大小最大32KB，键值对数量最多5条。超出此范围时返回错误码12800026。<br>说明：需注意IPC传输数据量的约束与限制，一次接口调用在IPC层的总传输数据量等于应用侧发送的数据量加系统层处理所需的必要数据量，因此实际可发送的最大数据量会小于32KB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。命令发送成功时resolve，失败时reject并返回BusinessError对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [12800026](../errorcode-inputmethod-framework.md#12800026-输入法系统面板错误) | input method system panel error. Possible causes:         1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons.         3. the caller is not system panel. |
