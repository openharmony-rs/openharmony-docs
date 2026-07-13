# UIAbilityContext

UIAbilityContext是需要保存状态的[UIAbility](arkts-app-ability-uiability.md)所对应的context，继承自[Context](arkts-ability-context-depr-i.md)，提供
UIAbility的相关配置信息以及操作UIAbility和ServiceExtensionAbility的方法，如启动UIAbility，停止当前UIAbilityContext所属的UIAbility，启动、停止、连接、断开连接
ServiceExtensionAbility等。

**继承/实现关系：** UIAbilityContext extends [Context](arkts-ability-context-t.md)

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## backToCallerAbilityWithResult

```TypeScript
backToCallerAbilityWithResult(abilityResult: AbilityResult, requestCode: string): Promise<void>
```

当通过
[startAbilityForResult](arkts-ability-uiabilitycontext-c.md#startabilityforresult-1)
或[openLink](arkts-ability-uiabilitycontext-c.md#openlink-1)拉起目标方UIAbility，且需要目标方返回结果时，目标方可以通过该接口将结果返回并拉起调用方。与
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
不同的是，本接口在返回时不会销毁当前UIAbility。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityResult | AbilityResult | 是 | 包含目标方返回给拉起方的结果。 |
| requestCode | string | 是 | 通过[startAbilityForResult](arkts-ability-uiabilitycontext-c.md#startabilityforresult-1)或[openLink](arkts-ability-uiabilitycontext-c.md#openlink-1)拉起目标方Ability且需要目标方返回结果时，系统生成的用于标识本次调用的requestCode。该值可以通过want中的[CALLER_REQUEST_CODE](arkts-app-ability-wantconstant.md)字段获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000074](../errorcode-ability.md#16000074-返回结果时requestcode对应的调用方不存在) | The caller does not exist. |
| [16000075](../errorcode-ability.md#16000075-不支持返回结果时拉起调用方) | BackToCaller is not supported. |

## connectAppServiceExtensionAbility

```TypeScript
connectAppServiceExtensionAbility(want: Want, callback: ConnectOptions): number
```

将当前UIAbility连接到
[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
。通过返回的proxy与AppServiceExtensionAbility进行通信，以使用AppServiceExtensionAbility对外提供的能力。仅支持在主线程调用。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 如果
> [AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
> 实例未启动，该接口的调用方必须为AppServiceExtensionAbility所属应用或者在AppServiceExtensionAbility支持的应用清单（即
> [extensionAbilities标签](../../../../quick-start/module-configuration-file.md#extensionabilities标签)的
> appIdentifierAllowList属性）中的应用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 连接[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)的Want信息。 |
| callback | ConnectOptions | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接id，[disconnectAppServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#disconnectappserviceextensionability-1)根据该连接id断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000201](../errorcode-ability.md#16000201-目标服务还未启动) | The target service has not been started yet. |

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

将当前UIAbility连接到一个[ServiceExtensionAbility](../../../../application-models/extensionability-overview.md)，通过返回的proxy与
ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 连接ServiceExtensionAbility的Want信息。 |
| options | ConnectOptions | 是 | 回调对象，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接id，调用方可以通过[disconnectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#disconnectserviceextensionability-2)传入该连接id来断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 10+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed.<br>**适用版本：** 10+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI.<br>**适用版本：** 10+ |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out.<br>**适用版本：** 10+ |

## connectUIServiceExtensionAbility

```TypeScript
connectUIServiceExtensionAbility(want: Want, callback: UIServiceExtensionConnectCallback) : Promise<UIServiceProxy>
```

连接一个UIServiceExtensionAbility。使用Promise异步回调。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 连接UIServiceExtensionAbility的必要信息。 |
| callback | UIServiceExtensionConnectCallback | 是 | 连接UIServiceExtensionAbility回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UIServiceProxy&gt; | Promise对象，包含connectUIServiceExtensionAbility执行后返回的[UIServiceProxy](arkts-ability-uiserviceproxy-i.md)对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |

## disconnectAppServiceExtensionAbility

```TypeScript
disconnectAppServiceExtensionAbility(connection: number): Promise<void>
```

断开与
[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
的连接。仅支持在主线程调用。使用Promise异步回调。
断开连接之后，为了防止使用可能失效的remote对象进行通信，建议将连接成功时返回的remote对象设置为null。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 在[connectAppServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectappserviceextensionability-1)返回的连接id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void
```

断开与[ServiceExtensionAbility](../../../../application-models/extensionability-overview.md)的连接，断开连接之后开发者需要将连接成功时返回的
remote对象置空。使用callback异步回调。仅支持在主线程调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 连接的ServiceExtensionAbility的标识id，即[connectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectserviceextensionability-1)返回的connectionId。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当断开与ServiceExtensionAbility的连接成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

断开与[ServiceExtensionAbility](../../../../application-models/extensionability-overview.md)的连接，断开连接之后开发者需要将连接成功时返回的
remote对象置空。使用Promise异步回调。仅支持在主线程调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 连接的ServiceExtensionAbility的标识id，即[connectServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectserviceextensionability-1)返回的connectionId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## disconnectUIServiceExtensionAbility

```TypeScript
disconnectUIServiceExtensionAbility(proxy: UIServiceProxy): Promise<void>
```

断开与UIServiceExtensionAbility的连接。使用Promise异步回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxy | UIServiceProxy | 是 | * [connectUIServiceExtensionAbility](arkts-ability-uiabilitycontext-c.md#connectuiserviceextensionability-1)执行返回的Proxy。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## hideAbility

```TypeScript
hideAbility(): Promise<void>
```

隐藏当前UIAbility。使用Promise异步回调。仅支持在主线程调用。
调用此接口前要求确保应用已添加至状态栏。
该接口仅在PC/2in1设备中、或处于[自由多窗模式](../../../../windowmanager/window-terminology.md#自由多窗模式)的Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed. |

## isTerminating

```TypeScript
isTerminating(): boolean
```

查询UIAbility是否处于消亡中状态。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否处于消亡中状态。true表示处于消亡中状态，false表示不处于消亡中状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## moveAbilityToBackground

```TypeScript
moveAbilityToBackground(): Promise<void>
```

将处于前台的UIAbility移动到后台。使用Promise异步回调。仅支持在主线程调用。<br/><!--RP1--><!--RP1End-->
从API version 12开始，该接口仅在Phone、Wearable和TV设备中可正常调用，在其他设备上返回16000061错误码。
从API version 13开始，该接口仅在Phone、Tablet、Wearable和TV设备中可正常调用，在其他设备上返回16000061错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16000065](../errorcode-ability.md#16000065-接口只支持ability在前台时调用) | The API can be called only when the ability is running in the foreground. |
| [16000066](../errorcode-ability.md#16000066--wukong模式不允许移动ability到前台后台) | An ability cannot switch to the foreground or background in Wukong mode. |

## openAtomicService

```TypeScript
openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<AbilityResult>
```

启动一个独立窗口的原子化服务。使用Promise异步回调。仅支持在主线程调用。
原子化服务被启动后，有如下情况：

- 正常情况下原子化服务可以通过
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身，并且返回结果给调用方。
- 异常情况下比如杀死原子化服务会返回异常结果给调用方，异常结果的resultCode为-1。
- 如果不同应用多次调用该接口启动同一个原子化服务，当这个原子化服务调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身时，只将正常结果返回给最后一个调用方, 其它调用方返回异常结果，异常结果中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的唯一标识，由云端统一分配。 |
| options | AtomicServiceOptions | 否 | 启动原子化服务所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，包含返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | The specified ID does not exist. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

## openLink

```TypeScript
openLink(link: string, options?: OpenLinkOptions, callback?: AsyncCallback<AbilityResult>): Promise<void>
```

通过<!--RP2-->[App Linking](../../../../application-models/app-linking-startup.md)<!--RP2End-->或
[Deep Linking](../../../../application-models/deep-linking-startup.md)方式启动UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用
Promise异步回调。仅支持在主线程调用。
通过在link字段中传入标准格式的URL，基于隐式want匹配规则拉起目标UIAbility。目标方必须同时具备以下过滤器特征，才能处理App Linking链接：

- "actions"列表中包含"ohos.want.action.viewData"。
- "entities"列表中包含"entity.system.browsable"。
- "uris"列表中包含"scheme"为"https"且"domainVerify"为true的元素。
如果希望获取被拉起方终止后的结果，可以设置callback参数，此参数的使用可参照
[startAbilityForResult](arkts-ability-uiabilitycontext-c.md#startabilityforresult-1)
接口。
传入的参数不合法时，如未设置必选参数或link字符串不是标准格式的URL，接口会直接抛出异常。参数校验通过，拉起目标方时出现的错误通过promise返回错误信息。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000136](../errorcode-ability.md#16000136-不允许通过app-linking方式拉起应用自身uiability) | The UIAbility is prohibited from launching itself via App Linking.<br>**适用版本：** 23+ |

## reportDrawnCompleted

```TypeScript
reportDrawnCompleted(callback: AsyncCallback<void>): void
```

用于通知系统UIAbility对应的窗口内容已经绘制完成。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当通知系统UIAbility对应的窗口内容已经绘制完成的操作成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## requestDialogService

```TypeScript
requestDialogService(want: Want, result: AsyncCallback<dialogRequest.RequestResult>): void
```

启动一个支持模态弹框的ServiceExtensionAbility。ServiceExtensionAbility被启动后，应用弹出模态弹框，通过调用
[setRequestResult](arkts-ability-requestcallback-i.md#setrequestresult-1)接口返回结果给调用者。
使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |
| result | AsyncCallback&lt;dialogRequest.RequestResult&gt; | 是 | 回调函数，当启动一个支持模态弹框的ServiceExtensionAbility成功，err中code为0，data为模态弹框请求结果；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |

## requestDialogService

```TypeScript
requestDialogService(want: Want): Promise<dialogRequest.RequestResult>
```

启动一个支持模态弹框的ServiceExtensionAbility。ServiceExtensionAbility被启动后，应用弹出模态弹框，通过调用
[setRequestResult](arkts-ability-requestcallback-i.md#setrequestresult-1)接口返回结果给调用者。
使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动ServiceExtensionAbility的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;dialogRequest.RequestResult&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |

## restartApp

```TypeScript
restartApp(want: Want): Promise<void>
```

处于获焦状态的UIAbility可以通过该接口，重启当前UIAbility所在的进程，并拉起应用内的指定UIAbility。仅支持主线程调用。使用Promise异步回调。
如果指定UIAbility就是当前UIAbility，则会刷新窗口至初始状态；如果是其他UIAbility，则会跳转并打开新的UIAbility窗口。
该接口仅在Phone设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 通过该接口重启进程时，不会触发进程中Ability的onDestroy生命周期回调。
>
> 在原子化服务调用本接口成功后的3秒内，再次调用本接口、
> [restartSelfAtomicService()](arkts-ability-restartselfatomicservice-f.md#restartselfatomicservice-1)或
> [ApplicationContext.restartApp()](arkts-ability-applicationcontext-c.md#restartapp-1)接口中的任一接口，系统将
> 返回错误码16000064。
>
> 在应用调用本接口成功后的3秒内，若再次调用本接口或
> [ApplicationContext.restartApp()](arkts-ability-applicationcontext-c.md#restartapp-1)接口中的任一接口，系统将
> 返回错误码16000064。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | Want类型参数，传入需要启动的UIAbility的信息，校验bundleName、abilityName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server error. |
| [16000063](../errorcode-ability.md#16000063-重启应用指定组件无效) | The target to restart does not belong to the caller or is not a UIAbility. |
| [16000064](../errorcode-ability.md#16000064-重启应用频繁) | Restart too frequently. |
| [16000065](../errorcode-ability.md#16000065-接口只支持ability在前台时调用) | The API can be called only when the ability is focused. |

## restoreWindowStage

```TypeScript
restoreWindowStage(localStorage: LocalStorage): void
```

恢复UIAbility中的WindowStage数据。仅支持在主线程调用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localStorage | LocalStorage | 是 | 用于恢复window stage的存储数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setAbilityInstanceInfo

```TypeScript
setAbilityInstanceInfo(label: string, icon: image.PixelMap): Promise<void>
```

设置当前UIAbility实例的图标和标签信息。图标与标签信息可在任务中心和快捷栏的界面中显示。使用Promise异步回调。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 15

**需要权限：** ohos.permission.SET_ABILITY_INSTANCE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 是 | 新的图标标签。标签长度不超过1024字节，且不可为空字符串。 |
| icon | image.PixelMap | 是 | 新的图标。建议图标大小为512px*512px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setColorMode

```TypeScript
setColorMode(colorMode: ConfigurationConstant.ColorMode): void
```

设置UIAbility的深浅色模式。调用该接口前需要保证该UIAbility对应页面已完成加载。仅支持主线程调用。

> **说明**：
>
> - 调用该接口前，需要确保窗口已完成创建、且UIAbility对应的页面已完成加载，即在
> [onWindowStageCreate()](arkts-ability-uiability-c.md#onwindowstagecreate-1)生命周期中通过
> [loadContent](../../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法加载页面之后调用。
>
> - 调用该接口后会创建新的资源管理器对象，如果此前有缓存资源管理器，需要进行更新。
>
> - 深浅色模式生效的优先级：UIAbility的深浅色模式 > 应用的深浅色模式（
> [ApplicationContext.setColorMode](arkts-ability-applicationcontext-c.md#setcolormode-1)）> 系统的深浅色模
> 式。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorMode | ConfigurationConstant.ColorMode | 是 | 设置颜色模式，包括: <br> - COLOR_MODE_DARK：深色模式 <br> - COLOR_MODE_LIGHT：浅色模式 <br> - COLOR_MODE_NOT_SET：不设置（跟随系统或应用） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## setMissionContinueState

```TypeScript
setMissionContinueState(state: AbilityConstant.ContinueState, callback: AsyncCallback<void>): void
```

设置UIAbility任务的流转状态。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | AbilityConstant.ContinueState | 是 | 流转状态。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当设置UIAbility任务的流转状态成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setMissionContinueState

```TypeScript
setMissionContinueState(state: AbilityConstant.ContinueState): Promise<void>
```

设置UIAbility任务的流转状态。使用Promise异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | AbilityConstant.ContinueState | 是 | 流转状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setMissionLabel

```TypeScript
setMissionLabel(label: string, callback: AsyncCallback<void>): void
```

设置UIAbility在多任务界面中显示的名称。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 是 | 任务的名称。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当设置UIAbility在多任务界面中显示的名称成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setMissionLabel

```TypeScript
setMissionLabel(label: string): Promise<void>
```

设置UIAbility在多任务界面中显示的名称。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 是 | 任务的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## setMissionWindowIcon

```TypeScript
setMissionWindowIcon(windowIcon: image.PixelMap): Promise<void>
```

设置当前UIAbility在应用窗口、任务中心应用卡片、快捷栏窗口快照的图标。使用Promise异步回调。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> setMissionWindowIcon<!--Del-->、
> [setMissionIcon](arkts-ability-uiabilitycontext-c-sys.md#setmissionicon-1)
> <!--DelEnd-->和
> [setAbilityInstanceInfo](arkts-ability-uiabilitycontext-c.md#setabilityinstanceinfo-1)之间不存在调用优先级关系。
> 当多个接口被依次调用时，后一次调用的接口所设置的图标信息将覆盖之前调用接口所设置的内容，最终生效的图标以最后一次调用的接口为准。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowIcon | image.PixelMap | 是 | 在应用窗口、任务中心应用卡片、快捷栏窗口快照显示的Ability图标。图标必须为正方形，且大小不能超过128M，否则返回401参数错误。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. 1. Connect to system service failed;2.System service failed to communicate with dependency module. |
| [16000135](../errorcode-ability.md#16000135-uiability的主窗不存在) | The main window of this ability not exist. |

## setOnNewWantSkipScenarios

```TypeScript
setOnNewWantSkipScenarios(scenarios: number): Promise<void>
```

在特定场景下拉起UIAbility时，如果不需要触发[onNewWant](arkts-ability-uiability-c.md#onnewwant-1)生命周期回调，可以通过该接口设置。仅支持在主线
程调用。使用Promise异步回调。

> **说明：**
>
> 该接口通常用于[onCreate](arkts-ability-uiability-c.md#oncreate-1)生命周期回调中。入参取值建议包含所有的
> [Scenarios](arkts-ability-scenarios-e.md)枚举值。详见下方示例代码。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scenarios | number | 是 | 取值范围请参考[Scenarios](arkts-ability-scenarios-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: Connection to service failed. |

## setRestoreEnabled

```TypeScript
setRestoreEnabled(enabled: boolean): void
```

设置UIAbility是否启用备份恢复。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 表示是否启用恢复。true表示启用，false表示不启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## showAbility

```TypeScript
showAbility(): Promise<void>
```

显示当前UIAbility。使用Promise异步回调。仅支持在主线程调用。
调用此接口前要求确保应用已添加至状态栏。
该接口仅在PC/2in1设备中、或处于[自由多窗模式](../../../../windowmanager/window-terminology.md#自由多窗模式)的Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed. |

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个UIAbility。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的必要信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0，message为空字符串；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API versiongreater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动一个UIAbility。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的必要信息。 |
| options | StartOptions | 是 | 启动UIAbility所携带的参数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0，message为空字符串；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 9+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag isforbidden.<br>**适用版本：** 9+ |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support.<br>**适用版本：** 12+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API versiongreater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed.<br>**适用版本：** 12+ |
| [16000068](../errorcode-ability.md#16000068-ability已经在运行中) | The ability is already running.<br>**适用版本：** 12+ |
| [16300003](../errorcode-ability.md#16300003-目标应用程序不是自身应用程序) | The target application is not the current application.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动一个UIAbility。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIAbility的必要信息。 |
| options | StartOptions | 否 | 启动UIAbility所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support.<br>**适用版本：** 12+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API versiongreater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed.<br>**适用版本：** 12+ |
| [16000068](../errorcode-ability.md#16000068-ability已经在运行中) | The ability is already running.<br>**适用版本：** 12+ |
| [16300003](../errorcode-ability.md#16300003-目标应用程序不是自身应用程序) | The target application is not the current application.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAbilityByCall

```TypeScript
startAbilityByCall(want: Want): Promise<Caller>
```

该接口用于获取[Caller](arkts-ability-caller-i.md)通信对象，以便于与
[Callee](arkts-ability-callee-i.md)进行通信。如果指定UIAbility未启动，则会将UIAbility启动至前台或后台。使用Promise异步回调。仅支持在主线程调
用。
该接口不支持拉起启动模式为[specified模式](../../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility。

> **说明：**
>
> - 跨设备场景下，调用方与目标方必须为同一应用。
>
> - 同设备场景下，要求调用方与目标方为不同应用，且调用方具备ohos.permission.ABILITY_BACKGROUND_COMMUNICATION权限（该权限仅系统应用可申请）。
>
> - 此外如果应用需要在后台调用该接口，需要具备ohos.permission.START_ABILITIES_FROM_BACKGROUND（该权限仅系统应用可申请）。更多的组件启动规则详见
> [组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。
> > **说明：**
>
> - API version 10及之前版本，需申请ohos.permission.ABILITY_BACKGROUND_COMMUNICATION（该权限仅系统应用可用）。
>
> - API version 11开始，仅需申请ohos.permission.DISTRIBUTED_DATASYNC（该权限仅当执行应用间建链操作时由软总线实施权限校验，在应用拉起阶段不做校验）。

**起始版本：** 9

**需要权限：** 
- API版本11+：ohos.permission.DISTRIBUTED_DATASYNC
- API版本9 - 10：ohos.permission.ABILITY_BACKGROUND_COMMUNICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 传入需要启动的UIAbility信息，包含abilityName、moduleName、bundleName、deviceId、parameters（可选）。将parameters中的'ohos.aafwk.param.callAbilityToForeground'配置为true可将UIAbility拉起到前台；否则表示将UIAbility拉起到后台。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Caller&gt; | Promise对象，获取要通讯的caller对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed.2.Sending restart message to system service failed. 3.System service failed to communicate with dependency module.4.Non-system applications are only allowed to call this interface across devices, not on the current device. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 9+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greaterthan 11.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void
```

通过type隐式启动[UIExtensionAbility](arkts-ability-uiextensionability-c.md)。使用callback异步回调。仅支持在主线
程调用，仅支持处于前台的应用调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 启动的UIExtensionAbility类型，取值详见[通过startAbilityByType接口拉起垂类面板](../../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | AbilityStartCallback | 是 | 回调函数，返回启动失败后的详细错误信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当接口调用成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11+ |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11+ |

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

通过type隐式启动[UIExtensionAbility](arkts-ability-uiextensionability-c.md)。使用Promise异步回调。仅支持在主线程
调用，仅支持处于前台的应用调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 启动的UIExtensionAbility类型，取值详见[通过startAbilityByType接口拉起垂类面板](../../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | AbilityStartCallback | 是 | 回调函数，返回启动失败后的详细错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11+ |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11+ |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用callback异步回调。仅支持在主线程调用。
UIAbility被启动后，有如下情况：

- 正常情况下可以通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身，并将结果返回给调用方。
- 异常情况下比如杀死UIAbility会将异常结果返回给调用方，异常结果中resultCode为-1。
- 如果被启动的UIAbility是[单实例模式](../../../../application-models/uiability-launch-type.md#singleton启动模式)，且这个UIAbility被不同应用多次调
用该接口启动，当这个UIAbility调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身时，只将正常结果返回给最后一个调用方，其它调用方返回异常结果，异常结果中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的必要信息。 |
| callback | AsyncCallback&lt;AbilityResult&gt; | 是 | 回调函数，当接口调用成功，err中code为0，data为被拉起方退出时的结果码和数据；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greaterthan 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用callback异步回调。仅支持在主线程调用。
UIAbility被启动后，有如下情况：

- 正常情况下可以通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身，并将结果返回给调用方。
- 异常情况下比如杀死UIAbility会将异常结果返回给调用方，异常结果中resultCode为-1。
- 如果被启动的UIAbility是[单实例模式](../../../../application-models/uiability-launch-type.md#singleton启动模式)，且这个UIAbility被不同应用多次调
用该接口启动，当这个UIAbility调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身时，只将正常结果返回给最后一个调用方，其它调用方返回异常结果，异常结果中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的必要信息。 |
| options | StartOptions | 是 | 启动Ability所携带的参数。 |
| callback | AsyncCallback&lt;AbilityResult&gt; | 是 | 回调函数，当接口调用成功，err中code为0，data为被拉起方退出时的结果码和数据；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 9+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag isforbidden.<br>**适用版本：** 9+ |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greaterthan 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

启动一个UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用Promise异步回调。仅支持在主线程调用。
UIAbility被启动后，有如下情况：

- 正常情况下可以通过调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身，并将结果返回给调用方。
- 异常情况下比如杀死UIAbility会将异常结果返回给调用方，异常结果中resultCode为-1。
- 如果被启动的UIAbility是[单实例模式](../../../../application-models/uiability-launch-type.md#singleton启动模式)，且这个UIAbility被不同应用多次调
用该接口启动，当这个UIAbility调用
[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)
接口销毁自身时，只将正常结果返回给最后一个调用方，其它调用方返回异常结果，异常结果中resultCode为-1。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的必要信息。 |
| options | StartOptions | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，包含返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greaterthan 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

## startAppServiceExtensionAbility

```TypeScript
startAppServiceExtensionAbility(want: Want): Promise<void>
```

启动
[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
实例。使用Promise异步回调。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 该接口的调用方必须为
> [AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
> 所属应用或者在AppServiceExtensionAbility支持的应用清单（即
> [extensionAbilities标签](../../../../quick-start/module-configuration-file.md#extensionabilities标签)的
> appIdentifierAllowList属性）中的应用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000200](../errorcode-ability.md#16000200-不允许该调用方启动应用后台服务) | The caller is not in the appIdentifierAllowList of the target application. |

## startSelfUIAbilityInCurrentProcess

```TypeScript
startSelfUIAbilityInCurrentProcess(want: Want, specifiedFlag: string, options?: StartOptions): Promise<void>
```

在当前进程中启动应用程序自己的UIAbility。
从API version 23开始，该接口仅在PC/2in1和Tablet设备中可正常调用，在其他设备中返回801错误码。
从API version 22开始，该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> - 只能冷启动目标UIAbility，如果目标UIAbility实例已经启动过，则启动失败。
>
> - 通过该接口启动的UIAbility实例，将运行在调用方所在的进程中。其他关于目标UIAbility的进程相关的策略（例如在
> [module.json5配置文件](../../../../quick-start/module-configuration-file.md)中通过isolationProcess或isolationMode字段来指定进程），均
> 不会生效。

> **说明**
> >
> -目标UIAability只能是冷启动的。如果目标UIAability的实例已经
> 启动，启动失败。
> >
> -通过此API启动的UIAbility实例与调用方在同一进程中运行。其他流程相关
> 目标UIAability的策略（例如通过**隔离进程**或**隔离模式**指定的策略）
> [module.json5](../../../../quick-start/module-configuration-file.md)文件中的字段不生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的必要信息。只支持[显式启动](../../../../application-models/explicit-implicit-want-mappings.md#显式want匹配原理)，不支持[隐式启动](../../../../application-models/explicit-implicit-want-mappings.md#隐式want匹配原理)。 |
| specifiedFlag | string | 是 | UIAbility的ID。此ID不得与任何已运行的ID重复- 开发者自定义的UIAbility标识。该标识不能与已启动的UIAbility标识相同，否则将返回错误。 <br>**说明：**<br>当通过该接口拉起启动模式为[specified](../../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility时，将不会触发[onAcceptWant](arkts-ability-abilitystage-c.md#onacceptwant-1)回调。 |
| options | StartOptions | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Connect to system service failed. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000122](../errorcode-ability.md#16000122-待启动的目标组件被系统管控模块拦截) | The target component is blocked by the system module anddoes not support startup. |
| [16000123](../errorcode-ability.md#16000123-不支持隐式启动) | Implicit startup is not supported. |
| [16000124](../errorcode-ability.md#16000124-不支持启动分布式uiability) | Starting a remote UIAbility is not supported. |
| [16000130](../errorcode-ability.md#16000130-uiability不属于调用方) | The UIAbility not belong to caller. |
| [16000131](../errorcode-ability.md#16000131-uiability已启动) | The UIAbility is already exist, can not start again. |

## startUIServiceExtensionAbility

```TypeScript
startUIServiceExtensionAbility(want: Want): Promise<void>
```

启动一个UIServiceExtensionAbility。使用Promise异步回调。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动UIServiceExtensionAbility的必要信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配应用) | No matching ability is found. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

## stopAppServiceExtensionAbility

```TypeScript
stopAppServiceExtensionAbility(want: Want): Promise<void>
```

停止
[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
实例。使用Promise异步回调。
该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

> **说明：**
>
> 该接口的调用方必须为
> [AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)
> 所属应用或者在AppServiceExtensionAbility支持的应用清单（即
> [extensionAbilities标签](../../../../quick-start/module-configuration-file.md#extensionabilities标签)的
> appIdentifierAllowList属性）中的应用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 停止[AppServiceExtensionAbility](../../../../reference/apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md)的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000200](../errorcode-ability.md#16000200-不允许该调用方启动应用后台服务) | The caller is not in the appIdentifierAllowList of the target application. |

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

销毁UIAbility自身。使用callback异步回调。仅支持在主线程调用。

> **说明：**
>
> 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置
> [removeMissionAfterTerminate](../../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当销毁UIAbility自身成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁UIAbility自身。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
>
> 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置
> [removeMissionAfterTerminate](../../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void
```

销毁UIAbility自身。使用callback异步回调。仅支持在主线程调用。
仅当UIAbility通过
[startAbilityForResult](arkts-ability-uiabilitycontext-c.md#startabilityforresult-1)
接口拉起时，调用terminateSelfWithResult接口销毁UIAbility，才会返回结果给调用方。

> **说明：**
>
> 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置
> [removeMissionAfterTerminate](../../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | AbilityResult | 是 | 返回给startAbilityForResult?接口调用方的相关信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当销毁UIAbility自身成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

销毁UIAbility自身。使用Promise异步回调。仅支持在主线程调用。
仅当UIAbility通过
[startAbilityForResult](arkts-ability-uiabilitycontext-c.md#startabilityforresult-1)
接口拉起时，调用terminateSelfWithResult接口销毁UIAbility，才会返回结果给调用方。

> **说明：**
>
> 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置
> [removeMissionAfterTerminate](../../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | AbilityResult | 是 | 返回给startAbilityForResult?接口调用方的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## abilityInfo

```TypeScript
abilityInfo: AbilityInfo
```

UIAbility的相关信息。

**类型：** AbilityInfo

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

应用运行时的环境变量，如语言、颜色模式等。

**类型：** Configuration

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

当前UIAbility所属HAP的信息。

**类型：** HapModuleInfo

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowStage

```TypeScript
windowStage: window.WindowStage
```

当前WindowStage对象。仅支持在主线程调用。

**类型：** window.WindowStage

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

