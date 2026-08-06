# UIExtensionContext

UIExtensionContext是[UIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的上下文环境，继承自 [ExtensionContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，提供UIExtensionAbility的相关配置信息以及操作UIAbility的方法，如 启动UIAbility等。

**继承/实现关系：** UIExtensionContext extends [ExtensionContext](extensioncontext-extensioncontext-c.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class UIExtensionContext extends ExtensionContext--><!--Device-unnamed-declare class UIExtensionContext extends ExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbilityWithRootHostToken

ArkTS-Dyn:
```TypeScript
connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): number
```

ArkTS-Sta:
```TypeScript
connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): long
```

将当前UIExtensionAbility连接到一个 [ServiceExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，通过返回的远 程代理对象与ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。与此同时，该方法会将UIExtensionAbility的原始宿主Ability的Token传 递给被连接的ServiceExtensionAbility，ServiceExtensionAbility可以在 [onCreate()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_或 [onConnect()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法中，通过Want参数的 [UI\_EXTENSION\_ROOT\_TOKEN]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_获取该Token。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): long--><!--Device-UIExtensionContext-connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称、Bundle名称等。 |
| connect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 返回连接标识ID，客户端可以通过 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. Possible cause:target service extension ability is in cross-device and needed designated permission to be started, but call ability do not have this permission. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system application |
| [16000001](../../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000008](../../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
| [16000053](../../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000070](../../errorcode-ability.md#16000070-严格模式下不允许该类型extension启动指定serviceextensionability) | The extension cannot start the service. |

## setHostPageOverlayForbidden

```TypeScript
setHostPageOverlayForbidden(isForbidden: boolean) : void
```

是否允许[UIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_拉起的页面被使用方的页面覆盖。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > > 该接口需要在窗口创建之前调用。建议在[UIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_的 > [onCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_生命周期内调用。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-setHostPageOverlayForbidden(isForbidden: boolean) : void--><!--Device-UIExtensionContext-setHostPageOverlayForbidden(isForbidden: boolean) : void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isForbidden | boolean | 是 | 是否允许[UIExtensionAbility]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_拉起的页面被使用方的页面覆盖。true表示不允许，false表示允许。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

## startAbilityForResultAsCaller

```TypeScript
startAbilityForResultAsCaller(want: Want, options?: StartOptions): Promise<AbilityResult>
```

使用设置的caller信息启动一个Ability，caller信息由want携带，在系统服务层识别，Ability可以在onCreate生命周期的want参数中获取到caller信息。使用该接口启动一个Ability时，want的 caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。使用Promise异步回调。 - 正常情况下可通过调用 [terminateSelfWithResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 接口使之终止并且返回结果给调用方。 - 异常情况下比如杀死Ability会返回异常信息给调用方，异常信息中resultCode为-1。 - 如果被启动的Ability模式是单实例模式，不同应用多次调用该接口启动这个Ability，当这个Ability调用 [terminateSelfWithResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 接口使之终止时，只将正常结果返回给最后一个调用方，其它调用方返回异常信息，异常信息中resultCode为-1。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-startAbilityForResultAsCaller(want: Want, options?: StartOptions): Promise<AbilityResult>--><!--Device-UIExtensionContext-startAbilityForResultAsCaller(want: Want, options?: StartOptions): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 启动Ability的want信息。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | Promise对象，返回Ability结果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000050](../../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000069](../../errorcode-ability.md#16000069-严格模式下不允许该类型extension启动三方应用) | The extension cannot start the third party application. |
| [16000070](../../errorcode-ability.md#16000070-严格模式下不允许该类型extension启动指定serviceextensionability) | The extension cannot start the service. |
| [16000073](../../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000071](../../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [16000072](../../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [16000076](../../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [16000077](../../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [16000078](../../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [16000079](../../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP\_\_\_ESCAPED\_UNDERSCORE\_\_\_INSTANCE\_\_\_ESCAPED\_UNDERSCORE\_\_\_KEY cannot be specified.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [16000080](../../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

启动一个ServiceExtensionAbility。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-startServiceExtensionAbility(want: Want): Promise<void>--><!--Device-UIExtensionContext-startServiceExtensionAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 启动ServiceExtensionAbility的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [16000050](../../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

## startServiceExtensionAbilityWithAccount

ArkTS-Dyn:
```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: int): Promise<void>
```

启动一个指定系统账号下的ServiceExtensionAbility。使用Promise异步回调。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > > 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-startServiceExtensionAbilityWithAccount(want: Want, accountId: int): Promise<void>--><!--Device-UIExtensionContext-startServiceExtensionAbilityWithAccount(want: Want, accountId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 启动ServiceExtensionAbility的Want信息。 |
| accountId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 系统账号的ID，可以通过[getOsAccountLocalId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [16000050](../../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

## startUIAbilities

```TypeScript
startUIAbilities(wantList: Array<Want>): Promise<void>
```

同时启动多个UIAbility。使用Promise异步回调。 开发者可以传入多个UIAbility对应的Want信息，这些UIAbility可以指向一个或多个应用。当所有的UIAbility都能启动成功时，系统会通过多个窗口同时展示这些UIAbility。根据窗口的处理，不同设备上可能会有不 同的展示效果（包括窗口形态、数量和排版布局）。 该接口仅在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-startUIAbilities(wantList: Array<Want>): Promise<void>--><!--Device-UIExtensionContext-startUIAbilities(wantList: Array<Want>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantList | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 是 | 需要被同时拉起的多个UIAbility的启动参数列表，最多支持传入4个Want。启动参数Want不支持隐式启动、跨用户启动、分布式、免安装和按需加载，不指明分身的情况下默认启动主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000073](../../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000076](../../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid. |
| [16000080](../../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported. |
| [16000120](../../errorcode-ability.md#16000120-wantlist内的元素个数超出4个或小于1个) | A maximum of four UIAbility instances can be started simultaneously.The current parameter exceeds the maximum number or is less than 1. |
| [16000121](../../errorcode-ability.md#16000121-待启动的目标组件类型不是uiability) | The target component type is not a UIAbility. |
| [16000122](../../errorcode-ability.md#16000122-待启动的目标组件被系统管控模块拦截) | The target component is blocked by the system module and does not support startup. |
| [16000123](../../errorcode-ability.md#16000123-不支持隐式启动) | Implicit startup is not supported. |
| [16000124](../../errorcode-ability.md#16000124-不支持启动分布式uiability) | Starting a remote UIAbility is not supported. |
| [16000125](../../errorcode-ability.md#16000125-不支持启动插件uiability) | Starting a plugin UIAbility is not supported. |
| [16000126](../../errorcode-ability.md#16000126-不支持启动dlp文件) | Starting DLP files is not supported. |

## startUIAbilitiesInSplitWindowMode

ArkTS-Dyn:
```TypeScript
startUIAbilitiesInSplitWindowMode(primaryWindowId: number, secondaryWant: Want): Promise<void>
```

ArkTS-Sta:
```TypeScript
startUIAbilitiesInSplitWindowMode(primaryWindowId: int, secondaryWant: Want): Promise<void>
```

当第一个UIAbility实例被创建后，启动第二个UIAbility，并以分屏模式进行显示。使用Promise异步回调。 该接口仅在Phone设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 如果第一个UIAbility实例被销毁，那么第二个UIAbility将以全屏模式启动。 > > 第二个UIAbility仅支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > > 如果调用方位于后台，还需要具备ohos.permission.START\_ABILITIES\_FROM\_BACKGROUND (该权限仅系统应用可申请)。 > > 组件启动规则详见：\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContext-startUIAbilitiesInSplitWindowMode(primaryWindowId: int, secondaryWant: Want): Promise<void>--><!--Device-UIExtensionContext-startUIAbilitiesInSplitWindowMode(primaryWindowId: int, secondaryWant: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primaryWindowId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 启动第一个UIAbility的主窗的窗口ID。窗口ID是\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的属性，WindowProperties可通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。 |
| secondaryWant | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 启动第二个UIAbility所需的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../../errorcode-ability.md#16000001-指定的ability名称不存在) | Target UIAbility does not exist. |
| [16000004](../../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../errorcode-ability.md#16000050-内部错误) | Failed to connect to the system service or system server handle failed. |
| [16000073](../../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000076](../../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid. |
| [16000080](../../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported. |
| [16000122](../../errorcode-ability.md#16000122-待启动的目标组件被系统管控模块拦截) | The target component is blocked by the system module and does not support startup. |
| [16000123](../../errorcode-ability.md#16000123-不支持隐式启动) | Implicit startup is not supported. |
| [16000124](../../errorcode-ability.md#16000124-不支持启动分布式uiability) | Starting a remote UIAbility is not supported. |
| [16000125](../../errorcode-ability.md#16000125-不支持启动插件uiability) | Starting a plugin UIAbility is not supported. |
| [16000126](../../errorcode-ability.md#16000126-不支持启动dlp文件) | Starting DLP files is not supported. |

