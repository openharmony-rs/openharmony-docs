# onSystemPanelStatusChange（系统接口）

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## onSystemPanelStatusChange

```TypeScript
function onSystemPanelStatusChange(callback: Callback<SystemPanelStatus>): void
```

订阅系统面板状态变化事件。当系统面板的输入类型、面板标志、底部抬高状态或功能按钮需求发生变化时，将触发回调通知。<br> <br>使用场景：当系统面板需要感知自身状态变化并做出相应调整（如根据输入类型切换面板布局、根据面板标志调整显示形态等）时使用此接口。<br> <br>使用后效果：订阅成功后，每当系统面板状态发生变化，系统将通过callback传入最新的[SystemPanelStatus](arkts-ime-inputmethodsystempanelmanager-systempanelstatus-i-sys.md)对象，包含当前输入类型、面板标志、底部抬高状态和功能按钮需求。<br> <br>前提条件：需先调用connectSystemChannel建立系统通道连接。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function onSystemPanelStatusChange(callback: Callback<SystemPanelStatus>): void--><!--Device-inputMethodSystemPanelManager-function onSystemPanelStatusChange(callback: Callback<SystemPanelStatus>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SystemPanelStatus](arkts-ime-inputmethodsystempanelmanager-systempanelstatus-i-sys.md)&gt; | 是 | 回调函数，当系统面板状态变化时触发。<br>使用场景：必须提供此回调函数以处理面板状态变化通知。<br>使用后效果：回调触发时，参数为[SystemPanelStatus](arkts-ime-inputmethodsystempanelmanager-systempanelstatus-i-sys.md)对象，开发者可根据其中各属性值调整面板的布局和行为。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
