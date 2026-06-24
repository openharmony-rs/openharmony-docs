# UIExtensionContext

UIExtensionContext是[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)的上下文环境，继承自
[ExtensionContext](arkts-ability-extensioncontext-c.md#ExtensionContext)，提供UIExtensionAbility的相关配置信息以及操作UIAbility的方法，如
启动UIAbility等。

**继承/实现关系：** UIExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md#ExtensionContext)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbilityWithRootHostToken

```TypeScript
connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): number
```

将当前UIExtensionAbility连接到一个
[ServiceExtensionAbility](arkts-ability-serviceextensionability-c-sys.md#onConnect-1)，通过返回的远
程代理对象与ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。与此同时，该方法会将UIExtensionAbility的原始宿主Ability的Token传
递给被连接的ServiceExtensionAbility，ServiceExtensionAbility可以在
[onCreate()](arkts-ability-serviceextensionability-c-sys.md#onCreate-1)或
[onConnect()](arkts-ability-serviceextensionability-c-sys.md#onConnect-1)方法中，通过Want参数的
[UI_EXTENSION_ROOT_TOKEN](arkts-ability-wantconstant-params-e.md#Params)获取该Token。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称、Bundle名称等。 |
| connect | ConnectOptions | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接标识ID，客户端可以通过<br/>[disconnectServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-inner-application-uiExtensionContext.md#disconnectserviceextensionability)<br/>传入该连接标识ID来断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. Possible cause:<br/>target service extension ability is in cross-device and needed designated permission to be started, but<br/>call ability do not have this permission. |
| [202](../../errorcode-universal.md#202-Not) | Not system application |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. Possible causes: 1. Connect to system service failed;<br/>2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service. |

## setHostPageOverlayForbidden

```TypeScript
setHostPageOverlayForbidden(isForbidden: boolean) : void
```

是否允许[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)拉起的页面被使用方的页面覆盖。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
>
> 该接口需要在窗口创建之前调用。建议在[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)的
> [onCreate](arkts-ability-uiextensionability-c.md#onCreate-1)生命周期内调用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForbidden | boolean | 是 | 是否允许[UIExtensionAbility](arkts-ability-uiextensionability-c.md#UIExtensionAbility)<br/>拉起的页面被使用方的页面覆盖。true表示不允许，false表示允许。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

## startAbilityForResultAsCaller

```TypeScript
startAbilityForResultAsCaller(want: Want, options?: StartOptions): Promise<AbilityResult>
```

使用设置的caller信息启动一个Ability，caller信息由want携带，在系统服务层识别，Ability可以在onCreate生命周期的want参数中获取到caller信息。使用该接口启动一个Ability时，want的
caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。使用Promise异步回调。

- 正常情况下可通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止并且返回结果给调用方。
- 异常情况下比如杀死Ability会返回异常信息给调用方，异常信息中resultCode为-1。
- 如果被启动的Ability模式是单实例模式，不同应用多次调用该接口启动这个Ability，当这个Ability调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateSelfWithResult-1)
接口使之终止时，只将正常结果返回给最后一个调用方，其它调用方返回异常信息，异常信息中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的want信息。 |
| options | StartOptions | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，返回Ability结果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-Not) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application. |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid. |
| [16000071](../../errorcode-universal.md#16000071-App) | App clone is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000072](../../errorcode-universal.md#16000072-App) | App clone or multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid.&lt;br&gt;**适用版本：** 14+ |
| [16000077](../../errorcode-universal.md#16000077-The) | The number of app instances reaches the limit.&lt;br&gt;**适用版本：** 14+ |
| [16000078](../../errorcode-universal.md#16000078-The) | The multi-instance is not supported.&lt;br&gt;**适用版本：** 14+ |
| [16000079](../../errorcode-universal.md#16000079-The) | The APP_INSTANCE_KEY cannot be specified.&lt;br&gt;**适用版本：** 14+ |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported.&lt;br&gt;**适用版本：** 14+ |

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

启动一个ServiceExtensionAbility。使用Promise异步回调。

**起始版本：** 18

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
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

启动一个指定系统账号下的ServiceExtensionAbility。使用Promise异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
>
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 18

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |
| accountId | number | 是 | 系统账号的ID，可以通过<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>接口获取。 |

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
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |

## startUIAbilities

```TypeScript
startUIAbilities(wantList: Array<Want>): Promise<void>
```

同时启动多个UIAbility。使用Promise异步回调。
开发者可以传入多个UIAbility对应的Want信息，这些UIAbility可以指向一个或多个应用。当所有的UIAbility都能启动成功时，系统会通过多个窗口同时展示这些UIAbility。根据窗口的处理，不同设备上可能会有不
同的展示效果（包括窗口形态、数量和排版布局）。
该接口仅在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantList | Array&lt;Want&gt; | 是 | 需要被同时拉起的多个UIAbility的启动参数列表，最多支持传入4个Want。启动参数Want不支持隐式启动、跨用户启动、分布式、免安装和按需加载，不指明分身的情况下默认<br/>启动主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid. |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid. |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported. |
| [16000120](../../errorcode-universal.md#16000120-A) | A maximum of four UIAbility instances can be started simultaneously.<br/>The current parameter exceeds the maximum number or is less than 1. |
| [16000121](../../errorcode-universal.md#16000121-The) | The target component type is not a UIAbility. |
| [16000122](../../errorcode-universal.md#16000122-The) | The target component is blocked by the system module and<br/>does not support startup. |
| [16000123](../../errorcode-universal.md#16000123-Implicit) | Implicit startup is not supported. |
| [16000124](../../errorcode-universal.md#16000124-Starting) | Starting a remote UIAbility is not supported. |
| [16000125](../../errorcode-universal.md#16000125-Starting) | Starting a plugin UIAbility is not supported. |
| [16000126](../../errorcode-universal.md#16000126-Starting) | Starting DLP files is not supported. |

## startUIAbilitiesInSplitWindowMode

```TypeScript
startUIAbilitiesInSplitWindowMode(primaryWindowId: number, secondaryWant: Want): Promise<void>
```

当第一个UIAbility实例被创建后，启动第二个UIAbility，并以分屏模式进行显示。使用Promise异步回调。
该接口仅在Phone设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 如果第一个UIAbility实例被销毁，那么第二个UIAbility将以全屏模式启动。
>
> 第二个UIAbility仅支持[显示启动](../../../../application-models/explicit-implicit-want-mappings.md#显式want匹配原理)。
>
> 如果调用方位于后台，还需要具备ohos.permission.START_ABILITIES_FROM_BACKGROUND (该权限仅系统应用可申请)。
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 21

**需要权限：** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primaryWindowId | number | 是 | 启动第一个UIAbility的主窗的窗口ID。窗口ID是<br/>[WindowProperties](../../../../reference/apis-arkui/arkts-apis-window-i.md#windowproperties)的属性，WindowProperties可通过<br/>[getWindowProperties()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9)获取。 |
| secondaryWant | Want | 是 | 启动第二个UIAbility所需的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [16000001](../../errorcode-universal.md#16000001-Target) | Target UIAbility does not exist. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Failed) | Failed to connect to the system service or system server handle failed. |
| [16000073](../../errorcode-universal.md#16000073-The) | The app clone index is invalid. |
| [16000076](../../errorcode-universal.md#16000076-The) | The app instance key is invalid. |
| [16000080](../../errorcode-universal.md#16000080-Creating) | Creating a new instance is not supported. |
| [16000122](../../errorcode-universal.md#16000122-The) | The target component is blocked by the system module and<br/>does not support startup. |
| [16000123](../../errorcode-universal.md#16000123-Implicit) | Implicit startup is not supported. |
| [16000124](../../errorcode-universal.md#16000124-Starting) | Starting a remote UIAbility is not supported. |
| [16000125](../../errorcode-universal.md#16000125-Starting) | Starting a plugin UIAbility is not supported. |
| [16000126](../../errorcode-universal.md#16000126-Starting) | Starting DLP files is not supported. |

