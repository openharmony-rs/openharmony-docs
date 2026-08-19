# WebNativeMessagingExtensionContext

WebNativeMessagingExtensionContext是Web原生消息扩展（ [WebNativeMessagingExtensionAbility](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md)）的运行上下文，继承自ExtensionContext，为 扩展Ability提供生命周期管理、Ability启动以及原生消息连接控制能力。开发者可在继承WebNativeMessagingExtensionAbility的扩展中通过`this.context`获取该上下文，进而调用 [startAbility](#startability)启动其他Ability、调用 [startAbilityForResult](#startabilityforresult)启动UIAbility并接收返回结果、调用 [terminateSelf](#terminateself)结束当前扩展，或调用 [stopNativeConnection](#stopnativeconnection)停止指定的Web原生消息连接。 > **说明:** > > 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** WebNativeMessagingExtensionContext extends ExtensionContext

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare class WebNativeMessagingExtensionContext--><!--Device-unnamed-declare class WebNativeMessagingExtensionContext-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

使用Promise异步回调启动Ability。如需获取启动的UIAbility退出时的返回结果，可以使用 [startAbilityForResult](#startabilityforresult)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>--><!--Device-WebNativeMessagingExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 表示需要启动的Ability的信息，包含bundleName、abilityName等属性，用于指定要启动的目标Ability。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动选项，用于指定目标UIAbility启动时的选项，包括但不局限于窗口模式、目标UIAbility启动时所在的屏幕等。当需要自定义启动配置时传入，不传入时使 用系统默认启动配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit. |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported. |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

启动一个UIAbility，使用Promise异步回调接收被拉起的UIAbility退出时的返回结果。 UIAbility被启动后，有如下情况: - 正常情况下可通过调用 [terminateSelfWithResult](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) 接口使之终止并且返回结果给调用方。 - 异常情况下比如销毁UIAbility会返回异常信息给调用方，异常信息中resultCode为-1。 - 只支持拉起自己应用的UIAbility。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionContext-startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>--><!--Device-WebNativeMessagingExtensionContext-startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 表示需要启动的UIAbility的信息，包含bundleName、abilityName等属性，用于指定要启动的目标UIAbility。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动选项，用于配置UIAbility的窗口模式等。当需要自定义启动配置时传入，不传入时使用系统默认启动配置。各字段默认值参考 [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md)说明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AbilityResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise对象，返回被启动方退出时的结果码和数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Instances cannot be created for other applications during inter-application startup. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | The application does not support appClone mode in multiAppMode. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled by the AppGallery and cannot be started. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by Enterprise Device Manager and cannot be started. |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit. |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The application does not support multiple instances. |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | The application does not support appClone and multi-instance mode in multiAppMode. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## stopNativeConnection

```TypeScript
stopNativeConnection(connectionId: int): Promise<void>
```

停止指定的本地连接。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionContext-stopNativeConnection(connectionId: int): Promise<void>--><!--Device-WebNativeMessagingExtensionContext-stopNativeConnection(connectionId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connectionId | int | 是 | 要停止的连接ID。取值范围为正整数，必须是有效的连接ID。当connectionId值无效时，会对应返回错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁当前Web原生消息扩展。该方法返回一个Promise对象用于异步处理，调用此方法会自动停止所有Web原生消息连接，无需再调用stopNativeConnection。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionContext-terminateSelf(): Promise<void>--><!--Device-WebNativeMessagingExtensionContext-terminateSelf(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

