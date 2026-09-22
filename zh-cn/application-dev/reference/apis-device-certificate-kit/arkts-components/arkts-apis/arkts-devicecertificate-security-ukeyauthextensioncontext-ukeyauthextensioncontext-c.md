# UkeyAuthExtensionContext

```TypeScript
declare class UkeyAuthExtensionContext extends ExtensionContext
```

UkeyAuthExtensionContext是UkeyAuthExtensionAbility的上下文，仅提供终止、报告绘制完成和颜色模式能力。它继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

**继承/实现关系：** UkeyAuthExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { UkeyAuthExtensionContext } from '@kit.DeviceCertificateKit';
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁此UkeyAuthExtensionAbility并关闭相应窗口。此API使用Promise返回结果。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回无值的Promise。 |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

销毁此UkeyAuthExtensionAbility，关闭相应窗口，并将结果返回给UkeyAuthExtensionAbility的调用方（通常为系统服务）。此API使用Promise返回结果。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给UkeyAuthExtensionAbility调用方的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回无值的Promise。 |
