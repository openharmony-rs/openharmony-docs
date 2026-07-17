# AVMusicTemplateController

音频模板控制器，可以获得音频模板控制器唯一的标识，用于与接入音频模板的媒体应用数据交互。

> **说明：**  
>  
> - 本模块仅适用于API version 23及以上版本的Car设备。

**起始版本：** 23

<!--Device-avMusicTemplate-class AVMusicTemplateController--><!--Device-avMusicTemplate-class AVMusicTemplateController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## clearSearchHistory

```TypeScript
clearSearchHistory(): Promise<OperResult>
```

清除搜索历史。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-clearSearchHistory(): Promise<OperResult>--><!--Device-AVMusicTemplateController-clearSearchHistory(): Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<OperResult> | Promise对象，返回清除搜索历史的操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## destroy

```TypeScript
destroy(): Promise<void>
```

销毁音频模板控制器。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-destroy(): Promise<void>--><!--Device-AVMusicTemplateController-destroy(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |

## downloadMediaEntity

```TypeScript
downloadMediaEntity(controlType: DownloadControlType, mediaEntity: MediaEntity): Promise<OperResult>
```

下载媒体实体。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-downloadMediaEntity(controlType: DownloadControlType, mediaEntity: MediaEntity): Promise<OperResult>--><!--Device-AVMusicTemplateController-downloadMediaEntity(controlType: DownloadControlType, mediaEntity: MediaEntity): Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlType | [DownloadControlType](arkts-avsession-avmusictemplate-downloadcontroltype-t.md) | 是 | 下载的控制类型。 |
| mediaEntity | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 是 | 媒体实体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<OperResult> | Promise对象，返回下载媒体实体的操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## executeAction

```TypeScript
executeAction(actionType: string, params: string): Promise<string>
```

执行动作。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-executeAction(actionType: string, params: string): Promise<string>--><!--Device-AVMusicTemplateController-executeAction(actionType: string, params: string): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | string | 是 | 动作类型。 |
| params | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象，返回执行动作的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## favoriteMediaEntity

```TypeScript
favoriteMediaEntity(actionType: MediaFavoriteType, mediaEntity: MediaEntity): Promise<OperResult>
```

收藏媒体。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-favoriteMediaEntity(actionType: MediaFavoriteType, mediaEntity: MediaEntity): Promise<OperResult>--><!--Device-AVMusicTemplateController-favoriteMediaEntity(actionType: MediaFavoriteType, mediaEntity: MediaEntity): Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | [MediaFavoriteType](arkts-avsession-avmusictemplate-mediafavoritetype-t.md) | 是 | 媒体收藏的类型。 |
| mediaEntity | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 是 | 媒体实体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<OperResult> | Promise对象，返回收藏媒体的操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## handleMemberPurchase

```TypeScript
handleMemberPurchase(info: MemberPurchaseInfo): Promise<DialogInfo>
```

处理购买会员情况。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-handleMemberPurchase(info: MemberPurchaseInfo): Promise<DialogInfo>--><!--Device-AVMusicTemplateController-handleMemberPurchase(info: MemberPurchaseInfo): Promise<DialogInfo>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [MemberPurchaseInfo](arkts-avsession-avmusictemplate-memberpurchaseinfo-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DialogInfo> | Promise对象，返回对话框信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## login

```TypeScript
login(controlType: LoginType, id?: string): Promise<QrCodeInfo[]>
```

登录。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-login(controlType: LoginType, id?: string): Promise<QrCodeInfo[]>--><!--Device-AVMusicTemplateController-login(controlType: LoginType, id?: string): Promise<QrCodeInfo[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlType | [LoginType](arkts-avsession-avmusictemplate-logintype-t.md) | 是 | 登录类型。 |
| id | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<QrCodeInfo[]> | Promise对象，返回二维码信息的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## offCurrentSingleChange

```TypeScript
offCurrentSingleChange(callback?: Callback<Single>): void
```

注销当前单曲改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offCurrentSingleChange(callback?: Callback<Single>): void--><!--Device-AVMusicTemplateController-offCurrentSingleChange(callback?: Callback<Single>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Single> | 否 | 回调函数，返回当前单曲的信息。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offCustomElementsChange

```TypeScript
offCustomElementsChange(callback?: ReportCustomElementsChangeEvent): void
```

注销上报自定义元素改变的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offCustomElementsChange(callback?: ReportCustomElementsChangeEvent): void--><!--Device-AVMusicTemplateController-offCustomElementsChange(callback?: ReportCustomElementsChangeEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportCustomElementsChangeEvent](arkts-avsession-avmusictemplate-reportcustomelementschangeevent-t.md) | 否 | 上报自定义元素改变事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offDialogCommandChange

```TypeScript
offDialogCommandChange(callback?: ReportDialogCommandEvent): void
```

注销对话框命令改变的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offDialogCommandChange(callback?: ReportDialogCommandEvent): void--><!--Device-AVMusicTemplateController-offDialogCommandChange(callback?: ReportDialogCommandEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportDialogCommandEvent](arkts-avsession-avmusictemplate-reportdialogcommandevent-t.md) | 否 | 上报对话框命令事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offDownloadMediaEntityStatusChange

```TypeScript
offDownloadMediaEntityStatusChange(callback?: Callback<MediaEntity>): void
```

注销上报下载媒体状态改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offDownloadMediaEntityStatusChange(callback?: Callback<MediaEntity>): void--><!--Device-AVMusicTemplateController-offDownloadMediaEntityStatusChange(callback?: Callback<MediaEntity>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MediaEntity> | 否 | 回调函数，返回媒体实体信息。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offExtensionAbilityChange

```TypeScript
offExtensionAbilityChange(callback?: ReportExecuteAbilityEvent): void
```

注销回调，用于停止监听拉起指定媒体应用的请求。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offExtensionAbilityChange(callback?: ReportExecuteAbilityEvent): void--><!--Device-AVMusicTemplateController-offExtensionAbilityChange(callback?: ReportExecuteAbilityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportExecuteAbilityEvent](arkts-avsession-avmusictemplate-reportexecuteabilityevent-t.md) | 否 | 通知音频模板控制方拉起指定的媒体应用界面的事件回调。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offMediaEntitiesChange

```TypeScript
offMediaEntitiesChange(callback?: Callback<MediaEntity[]>): void
```

注销媒体实体改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offMediaEntitiesChange(callback?: Callback<MediaEntity[]>): void--><!--Device-AVMusicTemplateController-offMediaEntitiesChange(callback?: Callback<MediaEntity[]>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MediaEntity[]> | 否 | 回调函数，返回媒体实体数组。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offPlaylistChange

```TypeScript
offPlaylistChange(callback?: Callback<PageMediaEntity>): void
```

注销上报播放列表改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offPlaylistChange(callback?: Callback<PageMediaEntity>): void--><!--Device-AVMusicTemplateController-offPlaylistChange(callback?: Callback<PageMediaEntity>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<PageMediaEntity> | 否 | 回调函数，返回标签页媒体实体信息。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offReportExecuteAction

```TypeScript
offReportExecuteAction(callback?: ReportExecuteActionEvent): void
```

注销上报执行动作的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offReportExecuteAction(callback?: ReportExecuteActionEvent): void--><!--Device-AVMusicTemplateController-offReportExecuteAction(callback?: ReportExecuteActionEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportExecuteActionEvent](arkts-avsession-avmusictemplate-reportexecuteactionevent-t.md) | 否 | 上报执行动作的事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offSettingsChange

```TypeScript
offSettingsChange(callback?: Callback<SettingItem[]>): void
```

注销上报设置改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offSettingsChange(callback?: Callback<SettingItem[]>): void--><!--Device-AVMusicTemplateController-offSettingsChange(callback?: Callback<SettingItem[]>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<SettingItem[]> | 否 | 回调函数，用于接收并处理设置项数组。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offTabContentChange

```TypeScript
offTabContentChange(callback?: ReportTabContentEvent): void
```

注销标签页内容改变的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offTabContentChange(callback?: ReportTabContentEvent): void--><!--Device-AVMusicTemplateController-offTabContentChange(callback?: ReportTabContentEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportTabContentEvent](arkts-avsession-avmusictemplate-reporttabcontentevent-t.md) | 否 | 上报标签页内容事件。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## offUserInfoChange

```TypeScript
offUserInfoChange(callback?: Callback<UserInfo>): void
```

注销用户信息改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-offUserInfoChange(callback?: Callback<UserInfo>): void--><!--Device-AVMusicTemplateController-offUserInfoChange(callback?: Callback<UserInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<UserInfo> | 否 | 回调函数，返回用户信息。不填该参数则注销该类型对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onCurrentSingleChange

```TypeScript
onCurrentSingleChange(callback: Callback<Single>): void
```

注册当前单曲改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onCurrentSingleChange(callback: Callback<Single>): void--><!--Device-AVMusicTemplateController-onCurrentSingleChange(callback: Callback<Single>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Single> | 是 | 回调函数，返回当前单曲的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onCustomElementsChange

```TypeScript
onCustomElementsChange(callback: ReportCustomElementsChangeEvent): void
```

注册上报自定义元素改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onCustomElementsChange(callback: ReportCustomElementsChangeEvent): void--><!--Device-AVMusicTemplateController-onCustomElementsChange(callback: ReportCustomElementsChangeEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportCustomElementsChangeEvent](arkts-avsession-avmusictemplate-reportcustomelementschangeevent-t.md) | 是 | 回调函数，上报自定义元素改变事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onDialogCommandChange

```TypeScript
onDialogCommandChange(callback: ReportDialogCommandEvent): void
```

注册对话框命令改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onDialogCommandChange(callback: ReportDialogCommandEvent): void--><!--Device-AVMusicTemplateController-onDialogCommandChange(callback: ReportDialogCommandEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportDialogCommandEvent](arkts-avsession-avmusictemplate-reportdialogcommandevent-t.md) | 是 | 回调函数，上报对话框命令事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onDownloadMediaEntityStatusChange

```TypeScript
onDownloadMediaEntityStatusChange(callback: Callback<MediaEntity>): void
```

注册上报下载媒体状态改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onDownloadMediaEntityStatusChange(callback: Callback<MediaEntity>): void--><!--Device-AVMusicTemplateController-onDownloadMediaEntityStatusChange(callback: Callback<MediaEntity>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MediaEntity> | 是 | 回调函数，返回媒体实体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onExtensionAbilityChange

```TypeScript
onExtensionAbilityChange(callback: ReportExecuteAbilityEvent): void
```

注册回调，当需要拉起指定媒体应用界面时触发。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onExtensionAbilityChange(callback: ReportExecuteAbilityEvent): void--><!--Device-AVMusicTemplateController-onExtensionAbilityChange(callback: ReportExecuteAbilityEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportExecuteAbilityEvent](arkts-avsession-avmusictemplate-reportexecuteabilityevent-t.md) | 是 | 回调函数，通知音频模板控制方拉起指定三方应用界面的事件，包含应用包名和界面名称等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onMediaEntitiesChange

```TypeScript
onMediaEntitiesChange(callback: Callback<MediaEntity[]>): void
```

注册媒体实体改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onMediaEntitiesChange(callback: Callback<MediaEntity[]>): void--><!--Device-AVMusicTemplateController-onMediaEntitiesChange(callback: Callback<MediaEntity[]>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<MediaEntity[]> | 是 | 回调函数，返回媒体实体数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onPlaylistChange

```TypeScript
onPlaylistChange(callback: Callback<PageMediaEntity>): void
```

注册上报播放列表改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onPlaylistChange(callback: Callback<PageMediaEntity>): void--><!--Device-AVMusicTemplateController-onPlaylistChange(callback: Callback<PageMediaEntity>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<PageMediaEntity> | 是 | 回调函数，返回标签页媒体实体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onReportExecuteAction

```TypeScript
onReportExecuteAction(callback: ReportExecuteActionEvent): void
```

注册上报执行动作的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onReportExecuteAction(callback: ReportExecuteActionEvent): void--><!--Device-AVMusicTemplateController-onReportExecuteAction(callback: ReportExecuteActionEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportExecuteActionEvent](arkts-avsession-avmusictemplate-reportexecuteactionevent-t.md) | 是 | 回调函数，上报对应按钮动作的事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onSettingsChange

```TypeScript
onSettingsChange(callback: Callback<SettingItem[]>): void
```

注册上报设置改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onSettingsChange(callback: Callback<SettingItem[]>): void--><!--Device-AVMusicTemplateController-onSettingsChange(callback: Callback<SettingItem[]>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<SettingItem[]> | 是 | 回调函数，返回设置项数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onTabContentChange

```TypeScript
onTabContentChange(callback: ReportTabContentEvent): void
```

注册标签页内容改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onTabContentChange(callback: ReportTabContentEvent): void--><!--Device-AVMusicTemplateController-onTabContentChange(callback: ReportTabContentEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ReportTabContentEvent](arkts-avsession-avmusictemplate-reporttabcontentevent-t.md) | 是 | 回调函数，上报标签页内容事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## onUserInfoChange

```TypeScript
onUserInfoChange(callback: Callback<UserInfo>): void
```

注册用户信息改变的回调。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-onUserInfoChange(callback: Callback<UserInfo>): void--><!--Device-AVMusicTemplateController-onUserInfoChange(callback: Callback<UserInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<UserInfo> | 是 | 回调函数，参数为用户信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |
| [35000012](../errorcode-avmusictemplate.md#35000012-音频模板错误) | AVMusicTemplate error. |

## playForSearch

```TypeScript
playForSearch(command: SearchPlayInfoType, args: SearchPlayInfo): Promise<OperResult>
```

搜播，支持音视频，示例仅以音频为例。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-playForSearch(command: SearchPlayInfoType, args: SearchPlayInfo): Promise<OperResult>--><!--Device-AVMusicTemplateController-playForSearch(command: SearchPlayInfoType, args: SearchPlayInfo): Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [SearchPlayInfoType](arkts-avsession-avmusictemplate-searchplayinfotype-e.md) | 是 |  |
| args | [SearchPlayInfo](arkts-avsession-avmusictemplate-searchplayinfo-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<OperResult> | Promise对象，返回操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## playMediaEntity

```TypeScript
playMediaEntity(mediaEntity: MediaEntity): Promise<void>
```

播放媒体。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-playMediaEntity(mediaEntity: MediaEntity): Promise<void>--><!--Device-AVMusicTemplateController-playMediaEntity(mediaEntity: MediaEntity): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaEntity | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 是 | 包含标题、作者等元数据的媒体实体对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryCompilation

```TypeScript
queryCompilation(compilationId: string, pageIndex: number): Promise<PageMediaEntity>
```

查询合集。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryCompilation(compilationId: string, pageIndex: int): Promise<PageMediaEntity>--><!--Device-AVMusicTemplateController-queryCompilation(compilationId: string, pageIndex: int): Promise<PageMediaEntity>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| compilationId | string | 是 | 合集的ID。 |
| pageIndex | number | 是 | 页索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PageMediaEntity> | Promise对象，返回查询的合集的分页对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryCompilationByKeyword

```TypeScript
queryCompilationByKeyword(keyword: string): Promise<Compilation[]>
```

按关键字查询合集。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryCompilationByKeyword(keyword: string): Promise<Compilation[]>--><!--Device-AVMusicTemplateController-queryCompilationByKeyword(keyword: string): Promise<Compilation[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyword | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Compilation[]> | Promise对象，返回合集数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryCurrentSingle

```TypeScript
queryCurrentSingle(): Promise<Single>
```

查询当前单曲。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryCurrentSingle(): Promise<Single>--><!--Device-AVMusicTemplateController-queryCurrentSingle(): Promise<Single>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Single> | Promise对象，返回当前单曲。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryCustomContent

```TypeScript
queryCustomContent(queryType: CustomType[]): Promise<CustomElement>
```

查询自定义内容。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryCustomContent(queryType: CustomType[]): Promise<CustomElement>--><!--Device-AVMusicTemplateController-queryCustomContent(queryType: CustomType[]): Promise<CustomElement>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryType | [CustomType](arkts-avsession-avmusictemplate-customtype-t.md)[] | 是 | 自定义类型数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<CustomElement> | Promise对象，返回查询的自定义元素。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryHotWords

```TypeScript
queryHotWords(): Promise<string[]>
```

查询热词。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryHotWords(): Promise<string[]>--><!--Device-AVMusicTemplateController-queryHotWords(): Promise<string[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string[]> | Promise对象，返回热词数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryMainTabs

```TypeScript
queryMainTabs(): Promise<MediaTab[]>
```

查询主标签。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryMainTabs(): Promise<MediaTab[]>--><!--Device-AVMusicTemplateController-queryMainTabs(): Promise<MediaTab[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<MediaTab[]> | Promise对象，返回查询的主标签页数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryMediaEntity

```TypeScript
queryMediaEntity(params: QueryMediaEntityParam): Promise<PageMediaEntity>
```

查询媒体实体。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryMediaEntity(params: QueryMediaEntityParam): Promise<PageMediaEntity>--><!--Device-AVMusicTemplateController-queryMediaEntity(params: QueryMediaEntityParam): Promise<PageMediaEntity>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [QueryMediaEntityParam](arkts-avsession-avmusictemplate-querymediaentityparam-i.md) | 是 | 查询媒体实体参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PageMediaEntity> | Promise对象，返回查询的媒体实体分页对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryMediaEntityByKeyword

```TypeScript
queryMediaEntityByKeyword(keyword: string, searchType: EntityType, pageIndex: number): Promise<PageMediaEntity>
```

按关键字查询媒体实体。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryMediaEntityByKeyword(keyword: string, searchType: EntityType, pageIndex: int): Promise<PageMediaEntity>--><!--Device-AVMusicTemplateController-queryMediaEntityByKeyword(keyword: string, searchType: EntityType, pageIndex: int): Promise<PageMediaEntity>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyword | string | 是 |  |
| searchType | [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md) | 是 | 媒体资源类型。 |
| pageIndex | number | 是 | 页索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PageMediaEntity> | Promise对象，返回与该关键字相关的媒体实体分页对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryMediaTabContent

```TypeScript
queryMediaTabContent(tabId: string): Promise<MediaTabContent>
```

查询媒体标签内容。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryMediaTabContent(tabId: string): Promise<MediaTabContent>--><!--Device-AVMusicTemplateController-queryMediaTabContent(tabId: string): Promise<MediaTabContent>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabId | string | 是 | 标签页ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<MediaTabContent> | Promise对象，返回媒体标签页内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryMemberPurchase

```TypeScript
queryMemberPurchase(memberPurchaseType: MemberPurchaseType): Promise<MemberPurchaseInfo[]>
```

查询购买会员的情况。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryMemberPurchase(memberPurchaseType: MemberPurchaseType): Promise<MemberPurchaseInfo[]>--><!--Device-AVMusicTemplateController-queryMemberPurchase(memberPurchaseType: MemberPurchaseType): Promise<MemberPurchaseInfo[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| memberPurchaseType | [MemberPurchaseType](arkts-avsession-avmusictemplate-memberpurchasetype-e.md) | 是 | 会员购买类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<MemberPurchaseInfo[]> | Promise对象，返回购买会员信息的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryPlaylist

```TypeScript
queryPlaylist(pageIndex: number, sort: Sort): Promise<PageMediaEntity>
```

查询播放列表。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryPlaylist(pageIndex: int, sort: Sort): Promise<PageMediaEntity>--><!--Device-AVMusicTemplateController-queryPlaylist(pageIndex: int, sort: Sort): Promise<PageMediaEntity>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pageIndex | number | 是 | 页索引。 |
| sort | [Sort](arkts-avsession-avmusictemplate-sort-e.md) | 是 | 查询到的播放列表数据的排序类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PageMediaEntity> | Promise对象，返回查询的播放列表的分页对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## queryRecommendMediaEntityList

```TypeScript
queryRecommendMediaEntityList(): Promise<MediaEntity[]>
```

查询推荐的媒体实体列表。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-queryRecommendMediaEntityList(): Promise<MediaEntity[]>--><!--Device-AVMusicTemplateController-queryRecommendMediaEntityList(): Promise<MediaEntity[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<MediaEntity[]> | Promise对象，返回推荐的媒体实体数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## querySearchHistory

```TypeScript
querySearchHistory(): Promise<string[]>
```

查询搜索历史。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-querySearchHistory(): Promise<string[]>--><!--Device-AVMusicTemplateController-querySearchHistory(): Promise<string[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string[]> | Promise对象，返回历史搜索词数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## reportProblemAndAdvice

```TypeScript
reportProblemAndAdvice(advice: string): Promise<OperResult>
```

报告问题和建议。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-reportProblemAndAdvice(advice: string): Promise<OperResult>--><!--Device-AVMusicTemplateController-reportProblemAndAdvice(advice: string): Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| advice | string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<OperResult> | Promise对象，返回报告问题和建议的操作结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## requestDialogInfo

```TypeScript
requestDialogInfo(actionType: DialogActionType, actionInfo?: DialogActionInfo): Promise<DialogInfo>
```

请求对话框信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-requestDialogInfo(actionType: DialogActionType, actionInfo?: DialogActionInfo): Promise<DialogInfo>--><!--Device-AVMusicTemplateController-requestDialogInfo(actionType: DialogActionType, actionInfo?: DialogActionInfo): Promise<DialogInfo>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | [DialogActionType](arkts-avsession-avmusictemplate-dialogactiontype-t.md) | 是 | 对话框操作类型。 |
| actionInfo | [DialogActionInfo](arkts-avsession-avmusictemplate-dialogactioninfo-i.md) | 否 | 对话框操作的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DialogInfo> | Promise对象，返回对话框信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## updateSettings

```TypeScript
updateSettings(settingItem: SettingItem): Promise<SettingItem>
```

更新设置信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-updateSettings(settingItem: SettingItem): Promise<SettingItem>--><!--Device-AVMusicTemplateController-updateSettings(settingItem: SettingItem): Promise<SettingItem>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settingItem | [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md) | 是 | 待更新的设置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<SettingItem> | Promise对象，返回更新后的设置项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | capability not supported. |
| [35000003](../errorcode-avmusictemplate.md#35000003-模板监听未注册) | Template listener not registered. |
| [35000005](../errorcode-avmusictemplate.md#35000005-音频模板不存在) | AVMusicTemplate does not exist. |
| [35000006](../errorcode-avmusictemplate.md#35000006-模板控制器不存在) | AVMusicTemplateController does not exist. |

## isDestroy

```TypeScript
isDestroy: boolean
```

音频模板控制器是否销毁。true表示已经销毁，false表示没有销毁。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-isDestroy: boolean--><!--Device-AVMusicTemplateController-isDestroy: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## sessionId

```TypeScript
sessionId: string
```

音频模板控制器唯一的标识。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMusicTemplateController-sessionId: string--><!--Device-AVMusicTemplateController-sessionId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

