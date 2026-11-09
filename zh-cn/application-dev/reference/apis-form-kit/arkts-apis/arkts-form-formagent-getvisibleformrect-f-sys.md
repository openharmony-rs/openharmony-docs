# getVisibleFormRect（系统接口）

## 导入模块

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## getVisibleFormRect

```TypeScript
function getVisibleFormRect(formId: string): Promise<formInfo.Rect>
```

获取可见卡片区域，使用Promise异步回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formAgent-function getVisibleFormRect(formId: string): Promise<formInfo.Rect>--><!--Device-formAgent-function getVisibleFormRect(formId: string): Promise<formInfo.Rect>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[formInfo.Rect](arkts-form-forminfo-rect-i.md)&gt; | Promise对象，返回卡片相对于屏幕左上角的位置和尺寸，单位为 vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
