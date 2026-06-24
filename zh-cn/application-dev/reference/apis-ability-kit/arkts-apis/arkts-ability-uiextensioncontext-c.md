# UIExtensionContext

UIExtensionContext是[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)的上下文环境，继承自
[ExtensionContext](arkts-ability-extensioncontext-c.md#ExtensionContext)，提供UIExtensionAbility的相关配置信息以及操作UIAbility的方法，如
启动UIAbility等。

**继承/实现关系：** UIExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md#ExtensionContext)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

将当前UIExtensionAbility连接到一个ServiceExtensionAbility，通过返回的proxy与ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility
对外提供的能力。
ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../../application-models/extensionability-overview.md)组件，这类组件由系
统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility可以被其他组件连接，并根据调用者的请求信息在后台处理相关事务。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称，Bundle名称等。 |
| options | ConnectOptions | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接id，客户端可以通过<br/>[disconnectServiceExtensionAbility](arkts-ability-uiextensioncontext-c.md#disconnectServiceExtensionAbility-2)传入该<br/>连接id来断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
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
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service. |

## connectUIServiceExtensionAbility

```TypeScript
connectUIServiceExtensionAbility(want: Want, callback: UIServiceExtensionConnectCallback) : Promise<UIServiceProxy>
```

连接到一个UIServiceExtensionAbility。使用Promise异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 用于连接的Want信息。 |
| callback | UIServiceExtensionConnectCallback | 是 | 连接UIServiceExtensionAbility回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UIServiceProxy&gt; | Promise对象，连接UIServiceExtensionAbility成功时，返回<br/>[UIServiceProxy](./application/UIServiceProxy:UIServiceProxy)对象，借助该对象可以往UIServiceExtensionAbility发送数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void
```

断开与ServiceExtensionAbility的连接，断开连接之后开发者需要将连接成功时返回的remote对象置空。使用callback异步回调。
ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../../application-models/extensionability-overview.md)组件，这类组件由系
统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility可以被其他组件连接，并根据调用者的请求信息在后台处理相关事务。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 连接的ServiceExtensionAbility的标识Id，即connectServiceExtensionAbility返回的connectionId。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当断开与ServiceExtensionAbility的连接成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

断开与ServiceExtensionAbility的连接，断开连接之后开发者需要将连接成功时返回的remote对象置空。使用Promise异步回调。
ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../../application-models/extensionability-overview.md)组件，这类组件由系
统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility可以被其他组件连接，并根据调用者的请求信息在后台处理相关事务。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 连接的ServiceExtensionAbility的标识Id，即<br/>[connectServiceExtensionAbility](arkts-ability-uiextensioncontext-c.md#connectServiceExtensionAbility-1)返回的connectionId。 |

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

## disconnectUIServiceExtensionAbility

```TypeScript
disconnectUIServiceExtensionAbility(proxy: UIServiceProxy): Promise<void>
```

断开UIServiceExtensionAbility。使用Promise异步回调。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxy | UIServiceProxy | 是 | * [connectUIServiceExtensionAbility](arkts-ability-uiextensioncontext-c.md#connectUIServiceExtensionAbility-1)返回的Proxy。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

## openAtomicService

```TypeScript
openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<AbilityResult>
```

打开一个独立窗口的原子化服务，并返回结果。使用Promise异步回调。
分为以下几种情况：

- 正常情况下可通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止并且返回结果给调用方。
- 异常情况下比如杀死原子化服务会返回异常信息给调用方，异常信息中resultCode为-1。
- 如果不同应用多次调用该接口启动同一个原子化服务，当这个原子化服务调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息，异常信息中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的唯一标识，由云端统一分配。 |
| options | AtomicServiceOptions | 否 | 启动原子化服务所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象。返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000003](../../errorcode-universal.md#16000003-The) | The specified ID does not exist. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |

## openLink

```TypeScript
openLink(link: string, options?: OpenLinkOptions, callback?: AsyncCallback<AbilityResult>): Promise<void>
```

通过App Linking或Deep Linking方式启动UIAbility。使用Promise异步回调。
通过在link字段中传入标准格式的URL，基于隐式want匹配规则拉起目标UIAbility。目标方必须具备以下过滤器特征，才能处理App Linking链接：

- "actions"列表中包含"ohos.want.action.viewData"。
- "entities"列表中包含"entity.system.browsable"。
- "uris"列表中包含"scheme"为"https"且"domainVerify"为true的元素。
如果希望获取被拉起方终止后的结果，可以设置callback参数，此参数的使用可参照
[startAbilityForResult](arkts-ability-uiextensioncontext-c.md#startAbilityForResult-1)
接口。
传入的参数不合法时，如未设置必选参数或link字符串不是标准格式的URL，接口会直接抛出异常。参数校验通过，拉起目标方时出现的错误通过promise返回错误信息。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| link | string | 是 | 指示要打开的标准格式URL。 |
| options | OpenLinkOptions | 否 | 打开URL的选项参数。 |
| callback | AsyncCallback&lt;AbilityResult&gt; | 否 | 回调函数，包含返回给拉起方的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
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
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found. |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000136](../../errorcode-universal.md#16000136-The) | The UIAbility is prohibited from launching itself via App Linking.&lt;br&gt;**适用版本：** 23+ |

## reportDrawnCompleted

```TypeScript
reportDrawnCompleted(callback: AsyncCallback<void>): void
```

用于应用通知系统UIExtensionAbility对应的窗口内容已绘制完成。系统会根据开发者调用的时机进行资源分配优化等，以优化应用启动及显示时间。使用callback异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当打点成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

## setColorMode

```TypeScript
setColorMode(colorMode: ConfigurationConstant.ColorMode): void
```

设置UIExtensionAbility的深浅色模式。调用该接口前需要保证该UIExtensionContext对应页面已完成加载。仅支持主线程调用。

> **说明**：
>
> - 调用该接口后会创建新的资源管理器对象，如果此前有缓存资源管理器，需要进行更新。
>
> - 深浅色模式生效的优先级：UIExtensionAbility的深浅色模式 > 应用的深浅色模式（
> [ApplicationContext.setColorMode](arkts-ability-applicationcontext-c.md#setColorMode-1)）> 系统的深浅色模
> 式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorMode | ConfigurationConstant.ColorMode | 是 | 设置颜色模式，包括：<br/>- COLOR_MODE_DARK：深色模式<br/>- COLOR_MODE_LIGHT：浅色模<br/>式<br/>- COLOR_MODE_NOT_SET：不设置（跟随系统或应用） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个UIAbility。使用callback异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility时必要的Want，包含待启动UIAbility的名称等信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当启动UIAbility成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
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
| [16000018](../../errorcode-universal.md#16000018-Redirection) | Redirection to a third-party application is not allowed in API version<br/>greater than 11.&lt;br&gt;**适用版本：** 12+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application.&lt;br&gt;**适用版本：** 12+ |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动一个UIAbility。使用callback异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility时必要的Want，包含待启动UIAbility的名称等信息。 |
| options | StartOptions | 是 | 启动UIAbility所携带的额外参数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当启动UIAbility成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
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
| [16000018](../../errorcode-universal.md#16000018-Redirection) | Redirection to a third-party application is not allowed in API version<br/>greater than 11.&lt;br&gt;**适用版本：** 12+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application.&lt;br&gt;**适用版本：** 12+ |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动一个UIAbility。使用Promise异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility时必要的Want，包含待启动UIAbility的名称等信息。 |
| options | StartOptions | 否 | 启动UIAbility所携带的额外参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
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
| [16000018](../../errorcode-universal.md#16000018-Redirection) | Redirection to a third-party application is not allowed in API version<br/>greater than 11.&lt;br&gt;**适用版本：** 12+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application.&lt;br&gt;**适用版本：** 12+ |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility，开发者可以通过回调函数接收被拉起的UIAbility退出时的返回结果。使用callback异步回调。UIAbility被启动后，有如下情况:

- 正常情况下可通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止并且返回结果给调用方。
- 异常情况下比如杀死UIAbility会返回异常信息给调用方, 异常信息中resultCode为-1。
- 如果被启动的UIAbility模式是单实例模式, 不同应用多次调用该接口启动这个UIAbility，当这个UIAbility调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息, 异常信息中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility时必要的Want，包含待启动UIAbility的名称等信息。 |
| callback | AsyncCallback&lt;AbilityResult&gt; | 是 | 回调函数，包含返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
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
| [16000018](../../errorcode-universal.md#16000018-Redirection) | Redirection to a third-party application is not allowed in API version<br/>greater than 11.&lt;br&gt;**适用版本：** 12+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application.&lt;br&gt;**适用版本：** 12+ |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility，开发者可以通过回调函数接收被拉起的UIAbility退出时的返回结果。使用callback异步回调。UIAbility被启动后，有如下情况:

- 正常情况下可通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止并且返回结果给调用方。
- 异常情况下比如杀死UIAbility会返回异常信息给调用方，异常信息中resultCode为-1。
- 如果被启动的UIAbility模式是单实例模式, 不同应用多次调用该接口启动这个UIAbility，当这个UIAbility调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止时，只将正常结果返回给最后一个调用方，其它调用方返回异常信息, 异常信息中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility时必要的Want，包含待启动UIAbility的名称等信息。 |
| options | StartOptions | 是 | 启动UIAbility所携带的额外参数。 |
| callback | AsyncCallback&lt;AbilityResult&gt; | 是 | 回调函数，包含返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
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
| [16000018](../../errorcode-universal.md#16000018-Redirection) | Redirection to a third-party application is not allowed in API version<br/>greater than 11.&lt;br&gt;**适用版本：** 12+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application.&lt;br&gt;**适用版本：** 12+ |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

启动一个UIAbility，开发者可以通过回调函数接收被拉起的UIAbility退出时的返回结果。使用Promise异步回调。UIAbility被启动后，有如下情况:

- 正常情况下可通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止并且返回结果给调用方。
- 异常情况下比如杀死UIAbility会返回异常信息给调用方, 异常信息中resultCode为-1。
- 如果被启动的UIAbility模式是单实例模式, 不同应用多次调用该接口启动这个UIAbility，当这个UIAbility调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止时，只将正常结果返回给最后一个调用方, 其它调用方返回异常信息, 异常信息中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility时必要的Want，包含待启动UIAbility的名称等信息。 |
| options | StartOptions | 否 | 启动UIAbility所携带的额外参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，返回被拉起的UIAbility退出时的返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
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
| [16000018](../../errorcode-universal.md#16000018-Redirection) | Redirection to a third-party application is not allowed in API version<br/>greater than 11.&lt;br&gt;**适用版本：** 12+ |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found.&lt;br&gt;**适用版本：** 12+ |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application.&lt;br&gt;**适用版本：** 12+ |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service.&lt;br&gt;**适用版本：** 12+ |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid.&lt;br&gt;**适用版本：** 12+ |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startUIServiceExtensionAbility

```TypeScript
startUIServiceExtensionAbility(want: Want): Promise<void>
```

启动一个UIServiceExtensionAbility。使用Promise异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIServiceExtensionAbility的Want。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

销毁UIExtensionAbility自身，同时关闭对应的窗口界面。使用callback异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。UIExtensionAbility停止成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁UIExtensionAbility自身，同时关闭对应的窗口界面。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void
```

销毁UIExtensionAbility自身，同时关闭对应的窗口界面，并将结果返回给UIExtensionAbility的拉起方，拉起方通常为系统服务。使用callback异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | AbilityResult | 是 | 返回给UIExtensionAbility拉起方的信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。UIExtensionAbility停止成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

销毁UIExtensionAbility自身，同时关闭对应的窗口界面，并将结果返回给UIExtensionAbility的拉起方，拉起方通常为系统服务。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | AbilityResult | 是 | 返回给UIExtensionAbility拉起方的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

