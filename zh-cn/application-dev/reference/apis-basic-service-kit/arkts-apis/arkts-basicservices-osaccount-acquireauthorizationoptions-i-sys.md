# AcquireAuthorizationOptions（系统接口）

表示获取授权的选项。

**起始版本：** 24

<!--Device-osAccount-interface AcquireAuthorizationOptions--><!--Device-osAccount-interface AcquireAuthorizationOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## challenge

```TypeScript
challenge?: Uint8Array
```

随机挑战值，可用于防止重放攻击，长度不得超过32字节，默认为undefined。

**类型：** Uint8Array

**默认值：** undefined

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationOptions-challenge?: Uint8Array--><!--Device-AcquireAuthorizationOptions-challenge?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## interactionContext

```TypeScript
interactionContext?: Context
```

用户交互上下文配置，默认为undefined。

- 未指定上下文时，授权对话框以模态系统模式显示。  
- 指定[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)或[UIExtensionContext](../apis-ability-kit/js-apis-inner-application-uiExtensionContext.md)时，以模态应用模式显示。  
- 未提供有效上下文时，授权对话框无法显示。

**注意**：仅当isInteractionAllowed为true时生效。

**类型：** Context

**默认值：** undefined, which means the authorization dialog will be displayed in modal system mode.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationOptions-interactionContext?: Context--><!--Device-AcquireAuthorizationOptions-interactionContext?: Context-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## isInteractionAllowed

```TypeScript
isInteractionAllowed?: boolean
```

是否允许用户交互，默认为true 。

如果为true，则允许在交互上下文中显示授权对话框；如果为false，则不允许显示授权对话框。

**注意**：此选项仅在调用者位于前台时生效。如果调用者在后台，则不允许用户交互。

**类型：** boolean

**默认值：** true

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationOptions-isInteractionAllowed?: boolean--><!--Device-AcquireAuthorizationOptions-isInteractionAllowed?: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## isReuseNeeded

```TypeScript
isReuseNeeded?: boolean
```

是否需要重复用先前的授权，默认为true。

如果为true且存在有效的授权结果，则将复用该结果；否则，将执行新的授权。

**类型：** boolean

**默认值：** true

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationOptions-isReuseNeeded?: boolean--><!--Device-AcquireAuthorizationOptions-isReuseNeeded?: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

