# ValidationCallback

```TypeScript
export type ValidationCallback = (context: ValidationContext) => boolean | Promise<boolean>
```

自定义远程验证。 该API使用Promise异步返回结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-http-export type ValidationCallback = (context: ValidationContext) => boolean | Promise<boolean>--><!--Device-http-export type ValidationCallback = (context: ValidationContext) => boolean | Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [ValidationContext](arkts-network-http-validationcontext-i.md) | 是 | 证书验证上下文，包含证书链、主机名和IP地址等信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean \| Promise&lt;boolean&gt; | 返回布尔值表示验证是否通过。true表示验证通过，false表示验证不通过。 支持返回Promise对象，用于异步验证场景。 |

