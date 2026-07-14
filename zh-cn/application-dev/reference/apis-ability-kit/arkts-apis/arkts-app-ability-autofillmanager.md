# @ohos.app.ability.autoFillManager

autoFillManager模块提供账号密码保存等功能。

不同于页面切换时触发的系统自动保存功能，该功能需要由用户手动触发。例如用户在网站上输入了账号密码，并点击“保存”按钮，才能触发相应的自动保存操作。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [requestAutoSave](arkts-ability-requestautosave-f.md#requestautosave-1) | 请求保存表单数据。使用callback异步回调。如果当前表单没有提供表单切换的功能，可以通过此接口保存历史表单输入数据，保存请求完成时会触发该回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AutoSaveCallback](arkts-ability-autosavecallback-i.md) | 当保存请求完成时所触发的回调接口。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [FillRequest](arkts-ability-fillrequest-t.md) | 自动填充的请求信息。 |
| [SaveRequest](arkts-ability-saverequest-t.md) | 自动保存的请求信息。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AutoFillPopupConfig](arkts-ability-autofillpopupconfig-t-sys.md) | 自动填充气泡弹窗的尺寸和位置信息。 |
| [AutoFillRect](arkts-ability-autofillrect-t-sys.md) | 用于自动填充的矩形区域。 |
| [CustomData](arkts-ability-customdata-t-sys.md) | 自定义数据。 |
| [FillRequestCallback](arkts-ability-fillrequestcallback-t-sys.md) | 自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。 |
| [FillResponse](arkts-ability-fillresponse-t-sys.md) | 自动填充的响应信息。 |
| [PageNodeInfo](arkts-ability-pagenodeinfo-t-sys.md) | 自动填充的页面节点信息。 |
| [PopupSize](arkts-ability-popupsize-t-sys.md) | 气泡弹窗的宽和高。 |
| [SaveRequestCallback](arkts-ability-saverequestcallback-t-sys.md) | 自动保存或者手动保存请求的回调对象。 |
| [UpdateRequest](arkts-ability-updaterequest-t-sys.md) | 自动填充的更新信息。 |
| [ViewData](arkts-ability-viewdata-t-sys.md) | 自动填充的视图数据信息。 |
<!--DelEnd-->

