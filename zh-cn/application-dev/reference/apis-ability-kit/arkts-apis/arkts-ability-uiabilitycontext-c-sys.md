# UIAbilityContext

UIAbilityContext是需要保存状态的[UIAbility](arkts-app-ability-uiability.md)所对应的context，继承自[Context](arkts-ability-context-depr-i.md#Context)，提供
UIAbility的相关配置信息以及操作UIAbility和ServiceExtensionAbility的方法，如启动UIAbility，停止当前UIAbilityContext所属的UIAbility，启动、停止、连接、断开连接
ServiceExtensionAbility等。

**继承/实现关系：** UIAbilityContext extends [Context](../../apis-arkui/arkts-apis/arkts-arkui-context-t.md#Context)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbilityWithAccount

```TypeScript
connectServiceExtensionAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number
```

将当前UIAbility连接到一个指定account的ServiceExtensionAbility。仅支持在主线程调用。
该接口在Phone、Tablet中可正常调用，在其他设备类型中返回16000006错误码。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| options | ConnectOptions | 是 | 与ServiceExtensionAbility建立连接后回调函数的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回Ability连接的结果code。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type.&lt;br&gt;**适用版本：** 10+ |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed.&lt;br&gt;**适用版本：** 10+ |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI.&lt;br&gt;**适用版本：** 10+ |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out.&lt;br&gt;**适用版本：** 10+ |

## requestModalUIExtension

```TypeScript
requestModalUIExtension(pickerWant: Want, callback: AsyncCallback<void>): void
```

请求在指定的前台应用上拉起对应类型的UIExtensionAbility。使用callback异步回调。仅支持在主线程调用。
其中，前台应用通过want.parameters中bundleName来指定，如果未指定前台应用、bundleName指定的应用未在前台或指定的前台应用的bundleName不正确，则在系统界面上直接拉起
UIExtensionAbility；被拉起的UIExtensionAbility通过want中bundleName、abilityName、moduleName字段共同确定，同时需要通过want.parameters中的
ability.want.params.uiExtensionType字段配置UIExtensionAbility的类型。
在前台应用上拉起UIExtensionAbility之前，必须确保该应用已完成页面初始化，否则将导致拉起失败、并出现"uiContent is nullptr"的报错信息。应用可通过监听页面加载状态来判断拉起
UIExtensionAbility的时机，页面初始化成功后会出现关键日志信息"UIContentImpl: focus again"。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerWant | Want | 是 | 拉起UIExtension的Want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当拉起UIExtension成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 11 - 11 |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist.&lt;br&gt;**适用版本：** 11 - 11 |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type.&lt;br&gt;**适用版本：** 11 - 11 |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 11 - 11 |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released.&lt;br&gt;**适用版本：** 11 - 11 |

## requestModalUIExtension

```TypeScript
requestModalUIExtension(pickerWant: Want): Promise<void>
```

请求在指定的前台应用上拉起对应类型的UIExtensionAbility。使用Promise异步回调。仅支持在主线程调用。
其中，前台应用通过want.parameters中bundleName来指定，如果未指定前台应用、bundleName指定的应用未在前台或指定的前台应用的bundleName不正确，则在系统界面上直接拉起
UIExtensionAbility；被拉起的UIExtensionAbility通过want中bundleName、abilityName、moduleName字段共同确定，同时需要通过want.parameters中的
ability.want.params.uiExtensionType字段配置UIExtensionAbility的类型。
在前台应用上拉起UIExtensionAbility之前，必须确保该应用已完成页面初始化，否则将导致拉起失败、并出现"uiContent is nullptr"的报错信息。应用可通过监听页面加载状态来判断拉起
UIExtensionAbility的时机，页面初始化成功后会出现关键日志信息"UIContentImpl: focus again"。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerWant | Want | 是 | 拉起UIExtension的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 11 - 11 |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist.&lt;br&gt;**适用版本：** 11 - 11 |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type.&lt;br&gt;**适用版本：** 11 - 11 |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 11 - 11 |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released.&lt;br&gt;**适用版本：** 11 - 11 |

## requestModalUIExtensionWithAccount

```TypeScript
requestModalUIExtensionWithAccount(pickerWant: Want, accountId: number): Promise<void>
```

请求指定的前台应用启动对应类型的UIExtensionAbility。
指定用户。该接口使用promise返回结果。它只能在主线程上调用。
> **说明**
> >
> 关于stage模型中组件的启动规则，请参见
> 【组件启动规则（阶段模型）】(../../../../application-models/component-startup-rules.md)。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerWant | Want | 是 | 需要用于启动UIExtensionAbility的信息 |
| accountId | number | 是 | 要请求的帐户<br/><br/>取值范围为全体整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. Possible causes: 1.Connect to system service failed;<br/>2.Send restart message to system service failed; 3.System service failed to communicate with dependency module.<br/>4.The logical screen corresponding to the specified accountId is not in the foreground. |

## setMissionIcon

```TypeScript
setMissionIcon(icon: image.PixelMap, callback: AsyncCallback<void>): void
```

设置当前UIAbility在任务中显示的图标，图标大小最大为600M。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | image.PixelMap | 是 | 在最近的任务中显示的UIAbility图标。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当设置当前UIAbility在任务中显示的图标成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api.&lt;br&gt;**适用版本：** 10+ |

## setMissionIcon

```TypeScript
setMissionIcon(icon: image.PixelMap): Promise<void>
```

设置当前UIAbility在任务中显示的图标, 图标大小最大为600M。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | image.PixelMap | 是 | 在最近的任务中显示的UIAbility图标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api.&lt;br&gt;**适用版本：** 10+ |

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, callback: AsyncCallback<void>): void
```

使用设置的caller信息启动一个UIAbility，caller信息由want携带，在系统服务层识别，UIAbility可以在onCreate生命周期的want参数中获取到caller信息。使用该接口启动一个UIAbility时
，want的caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

使用设置的caller信息启动一个UIAbility，caller信息由want携带，在系统服务层识别，UIAbility可以在onCreate生命周期的want参数中获取到caller信息。使用该接口启动一个UIAbility时
，want的caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| options | StartOptions | 是 | 启动UIAbility所携带的参数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options?: StartOptions): Promise<void>
```

使用设置的caller信息启动一个UIAbility，caller信息由want携带，在系统服务层识别，UIAbility可以在onCreate生命周期的want参数中获取到caller信息。使用该接口启动一个UIAbility时
，want的caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| options | StartOptions | 否 | 启动UIAbility所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityByCallWithAccount

```TypeScript
startAbilityByCallWithAccount(want: Want, accountId: number): Promise<Caller>
```

根据accountId对指定的UIAbility进行call调用，并且可以使用返回的Caller通信接口与被调用方进行通信。仅支持在主线程调用。使用Promise异步回调。
该接口不支持拉起启动模式为[specified模式](../../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility。
使用规则：

- 跨用户场景下，Call调用目标UIAbility时，调用方应用需同时申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`与`
ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS`权限。
- 调用方应用位于后台时，使用该接口启动UIAbility需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。
- 跨应用场景下，目标UIAbility的exported属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限。
- 同设备与跨设备场景下，该接口的使用规则存在差异，详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**需要权限：** ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 传入需要启动的UIAbility的信息，包含abilityName、moduleName、bundleName、deviceId(可选)、parameters(可选)，其中deviceId缺省或<br/>为空表示启动本地UIAbility，parameters缺省或为空表示后台启动UIAbility。 |
| accountId | number | 是 | 系统账号的账号ID，-1表示当前活动用户，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Caller&gt; | Promise对象，返回要通讯的caller对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityForResultWithAccount

```TypeScript
startAbilityForResultWithAccount(want: Want, accountId: number, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility并在该UIAbility销毁时返回执行结果。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| callback | AsyncCallback&lt;AbilityResult&gt; | 是 | 回调函数，当接口调用成功，err中code为0，data为被拉起的UIAbility销毁时的结果码和数据；否则err会返回对应的错误码和错<br/>误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityForResultWithAccount

```TypeScript
startAbilityForResultWithAccount(
    want: Want,
    accountId: number,
    options: StartOptions,
    callback: AsyncCallback<void>
  ): void
```

启动一个UIAbility并在该UIAbility销毁时返回执行结果。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| options | StartOptions | 是 | 启动UIAbility所携带的参数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type.&lt;br&gt;**适用版本：** 9 - 9 |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is<br/>forbidden.&lt;br&gt;**适用版本：** 9 - 9 |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityForResultWithAccount

```TypeScript
startAbilityForResultWithAccount(want: Want, accountId: number, options?: StartOptions): Promise<AbilityResult>
```

启动一个UIAbility并在该UIAbility销毁时返回执行结果。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| options | StartOptions | 否 | 启动UIAbility所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，包含AbilityResult参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

根据want和accountId启动UIAbility。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, options: StartOptions, callback: AsyncCallback<void>): void
```

根据want、accountId及startOptions启动UIAbility。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| options | StartOptions | 是 | 启动UIAbility所携带的参数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type.&lt;br&gt;**适用版本：** 9 - 9 |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is<br/>forbidden.&lt;br&gt;**适用版本：** 9 - 9 |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, options?: StartOptions): Promise<void>
```

根据want、accountId和startOptions启动UIAbility。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| options | StartOptions | 否 | 启动UIAbility所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个指定的UIAbility，如果这个UIAbility有多个实例，将拉起最近启动的那个实例。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> - 跨设备场景下，调用方与目标方必须为同一应用，且该应用需要具备ohos.permission.DISTRIBUTED_DATASYNC权限，才能启动成功。
>
> - 跨应用场景下，目标UIAbility的visible属性若配置为false，调用方应用需申请ohos.permission.START_INVISIBLE_ABILITY权限。
>
> - 如果指定的UIAbility有多个实例，调用方应用需申请ohos.permission.START_RECENT_ABILITY权限（该权限仅系统应用可申请），才能拉起最近启动的那个实例。
>
> - 如果调用方位于后台，还需要具备ohos.permission.START_ABILITIES_FROM_BACKGROUND（该权限仅系统应用可申请）。
> 更多的组件启动规则详见[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 需要启动UIAbility的Want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api.&lt;br&gt;**适用版本：** 14+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动一个指定的UIAbility。如果这个UIAbility有多个实例，将拉起最近启动的那个实例。当开发者需要携带启动参数时可以选择此API。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> - 跨设备场景下，调用方与目标方必须为同一应用，且该应用需要具备ohos.permission.DISTRIBUTED_DATASYNC权限，才能启动成功。
>
> - 跨应用场景下，目标UIAbility的visible属性若配置为false，调用方应用需申请ohos.permission.START_INVISIBLE_ABILITY权限。
>
> - 如果指定的UIAbility有多个实例，调用方应用需申请ohos.permission.START_RECENT_ABILITY权限（该权限仅系统应用可申请），才能拉起最近启动的那个实例。
>
> - 如果调用方位于后台，还需要具备ohos.permission.START_ABILITIES_FROM_BACKGROUND（该权限仅系统应用可申请）。
> 更多的组件启动规则详见[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 需要启动UIAbility的Want信息。 |
| options | StartOptions | 是 | 启动UIAbility所携带的参数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type.&lt;br&gt;**适用版本：** 9 - 9 |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is<br/>forbidden.&lt;br&gt;**适用版本：** 9 - 9 |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api.&lt;br&gt;**适用版本：** 14+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, options?: StartOptions): Promise<void>
```

启动一个指定的UIAbility。如果这个UIAbility有多个实例，将拉起最近启动的那个实例。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> - 跨设备场景下，调用方与目标方必须为同一应用，且该应用需要具备ohos.permission.DISTRIBUTED_DATASYNC权限，才能启动成功。
>
> - 跨应用场景下，目标UIAbility的visible属性若配置为false，调用方应用需申请ohos.permission.START_INVISIBLE_ABILITY权限。
>
> - 如果指定的UIAbility有多个实例，调用方应用需申请ohos.permission.START_RECENT_ABILITY权限（该权限仅系统应用可申请），才能拉起最近启动的那个实例。
>
> - 如果调用方位于后台，还需要具备ohos.permission.START_ABILITIES_FROM_BACKGROUND（该权限仅系统应用可申请）。
> 更多的组件启动规则详见[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 需要启动UIAbility的Want信息。 |
| options | StartOptions | 否 | 启动UIAbility所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api.&lt;br&gt;**适用版本：** 14+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个新的ServiceExtensionAbility。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

启动一个新的ServiceExtensionAbility。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

启动一个新的ServiceExtensionAbility。使用callback异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

启动一个新的ServiceExtensionAbility。使用Promise异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want, callback: AsyncCallback<void>): void
```

停止指定的ServiceExtensionAbility后台服务。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 停止ServiceExtensionAbility的Want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当停止ServiceExtensionAbility的接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 10+ |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled.&lt;br&gt;**适用版本：** 10+ |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM.&lt;br&gt;**适用版本：** 10+ |

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want): Promise<void>
```

停止同一应用程序内的服务。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 停止ServiceExtensionAbility的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface.&lt;br&gt;**适用版本：** 10+ |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |

## stopServiceExtensionAbilityWithAccount

```TypeScript
stopServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

停止同一应用程序内指定账户的服务。使用callback异步回调。

> **说明：**
>
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 停止ServiceExtensionAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当停止ServiceExtensionAbility的接口调用成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |

## stopServiceExtensionAbilityWithAccount

```TypeScript
stopServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

停止同一应用程序内指定账户的服务。使用Promise异步回调。

> **说明：**
>
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 停止ServiceExtensionAbility的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component.&lt;br&gt;**适用版本：** 10+ |

