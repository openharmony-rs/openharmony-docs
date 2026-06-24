# AutoFillExtensionContext（系统接口）

AutoFillExtensionContext模块是AutoFillExtensionAbility的上下文环境，继承自
[ExtensionContext](arkts-ability-extensioncontext-c.md#ExtensionContext)。

**继承/实现关系：** AutoFillExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md#ExtensionContext)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## reloadInModal

```TypeScript
reloadInModal(customData: CustomData): Promise<void>
```

拉起模态页面。使用Promise异步回调。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customData | CustomData | 是 | 拉起模态页面时的自定义信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Not) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-If) | If the input parameter is not valid parameter. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

