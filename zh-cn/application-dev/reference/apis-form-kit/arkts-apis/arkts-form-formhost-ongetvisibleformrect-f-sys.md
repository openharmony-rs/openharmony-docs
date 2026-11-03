# onGetVisibleFormRect（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## onGetVisibleFormRect

```TypeScript
function onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void
```

订阅请求可见widget位置和尺寸事件。该接口使用异步回调返回结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void--><!--Device-formHost-function onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [formInfo.GetFormRectInfoCallback](arkts-form-forminfo-getformrectinfocallback-t-sys.md) | 是 | widget host处理的回调函数。请求并返回小部件相对于屏幕左上角的位置和尺寸。单位为vp。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
