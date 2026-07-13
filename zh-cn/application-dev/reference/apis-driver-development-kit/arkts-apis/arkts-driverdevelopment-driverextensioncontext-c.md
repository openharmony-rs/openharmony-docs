# DriverExtensionContext

DriverExtensionContext模块是DriverExtensionAbility的上下文环境，继承自ExtensionContext。
DriverExtensionContext模块提供DriverExtensionAbility实现中需要主动发起的操作。

> **说明：**
> - 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** DriverExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.Driver.ExternalDevice

## updateDriverState

```TypeScript
updateDriverState(): void
```

驱动状态上报。预留接口，暂不提供具体功能。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Driver.ExternalDevice

