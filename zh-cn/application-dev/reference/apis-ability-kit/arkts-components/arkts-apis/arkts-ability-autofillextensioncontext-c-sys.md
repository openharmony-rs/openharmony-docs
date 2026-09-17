# AutoFillExtensionContext（系统接口）

AutoFillExtensionContext模块是AutoFillExtensionAbility的上下文环境，继承自[ExtensionContext](arkts-ability-extensioncontext-c.md)。

**继承/实现关系：** AutoFillExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## reloadInModal

```TypeScript
reloadInModal(customData: CustomData): Promise<void>
```

重新拉起模态页面。使用Promise异步回调。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customData | [CustomData](arkts-ability-customdata-i-sys.md) | 是 | 拉起模态页面时的自定义信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
通过点击账号密码输入框触发自动填充服务时，在[AutoFillExtensionAbility](arkts-ability-app-ability-autofillextensionability-autofillextensionability-c-sys.md)的onFillRequest生命周期中拉起账号选择界面。

当点击账号选择界面选择任意账号时，调用reloadInModal接口再次触发自动填充服务，在AutoFillExtensionAbility的onFillRequest生命周期中拉起模态页面。
```

```TypeScript
当点击账号选择界面选择任意账号时，调用reloadInModal接口。
```
