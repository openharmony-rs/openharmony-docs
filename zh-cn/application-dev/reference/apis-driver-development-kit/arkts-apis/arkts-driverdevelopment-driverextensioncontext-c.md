# DriverExtensionContext

DriverExtensionContext模块是DriverExtensionAbility的上下文环境，继承自ExtensionContext。DriverExtensionContext模块提供DriverExtensionAbility实现中需要主动发起的操作。

> **说明：**
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** DriverExtensionContext extends ExtensionContext

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

**示例**

```TypeScript
// 当前代码实现依赖上一节代码实现
if (context !== undefined) {
  context.updateDriverState();
}
```
