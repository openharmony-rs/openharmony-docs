# WindowExtensionContext（系统接口）

WindowExtensionContext模块是WindowExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

WindowExtensionContext模块提供[WindowExtensionAbility](arkts-application-windowextensionability.md)具有的能力，包括启动Ability。

> **说明：**  
>  
> - 从API version 21开始废弃，推荐使用[UIExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensioncontext-c.md)。  
>  
> - 本模块接口为系统接口。  
>  
> - 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** WindowExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 9

**废弃版本：** 21

<!--Device-unnamed-declare class WindowExtensionContext extends ExtensionContext--><!--Device-unnamed-declare class WindowExtensionContext extends ExtensionContext-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动Ability，使用callback异步回调。

> **说明：**  
>  
> - 从API version 9开始支持，从API version 21开始废弃，推荐使用  
> [UIExtensionContext.startability](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensioncontext-c.md#startability-2)  
> 。

**起始版本：** 9

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionContext-startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void--><!--Device-WindowExtensionContext-startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | callback形式返回启动结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动Ability，使用Promise异步回调。

> **说明：**  
>  
> - 从API version 9开始支持，从API version 21开始废弃，推荐使用  
> [UIExtensionContext.startability](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensioncontext-c.md#startability-3)  
> 。

**起始版本：** 9

**废弃版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>--><!--Device-WindowExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-arkui-want-t-sys.md) | 是 | Want类型参数，传入需要启动的ability的信息，如Ability名称，Bundle名称等。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

