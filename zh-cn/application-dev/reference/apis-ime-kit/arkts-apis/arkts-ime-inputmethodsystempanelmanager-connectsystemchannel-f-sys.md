# connectSystemChannel（系统接口）

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## connectSystemChannel

```TypeScript
function connectSystemChannel(): Promise<void>
```

连接系统通道，用于建立输入法系统面板和系统预置输入法应用之间的通信连接。仅允许系统预置输入法面板调用。<br> <br>含义/功能：建立系统面板与系统预置输入法应用之间的通信通道，为后续的私有命令收发和面板状态同步提供连接基础。<br> <br>使用场景：当系统面板需要与系统预置输入法应用进行私有命令通信或面板状态同步时，必须先调用此接口建立通信通道。<br> <br>使用后效果：连接成功后，系统面板与输入法应用之间的通信通道建立，后续可调用sendPrivateCommand、onSystemPrivateCommand和onSystemPanelStatusChange等接口进行数据通信和状态同步。<br> <br>前提条件：需具有ohos.permission.CONNECT_IME_ABILITY权限，且调用者必须是系统应用和系统预置输入法面板。<br> <br>相关接口间的配合/制约关系：本接口是使用本模块其他通信接口的前提，必须先调用connectSystemChannel建立通道后，才能使用sendPrivateCommand、onSystemPrivateCommand和onSystemPanelStatusChange等接口。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function connectSystemChannel(): Promise<void>--><!--Device-inputMethodSystemPanelManager-function connectSystemChannel(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。连接成功时resolve，失败时reject并返回BusinessError对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible causes: a system error, such as null pointer, IPC exception. |
| [12800026](../errorcode-inputmethod-framework.md#12800026-输入法系统面板错误) | input method system panel error. Possible causes:         1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons.         3. the caller is not system panel. |
