# DriverExtensionContext

DriverExtensionContext模块是DriverExtensionAbility的上下文环境，继承自ExtensionContext。 DriverExtensionContext模块提供DriverExtensionAbility实现中需要主动发起的操作。

## 使用说明 在使用DriverExtensionContext的功能前，需要通过DriverExtensionAbility子类实例获取。 ```ts let context: DriverExtensionContext | undefined; class EntryAbility extends DriverExtensionAbility { onInit() { context = this.context; // 获取DriverExtensionContext } } ```

**继承/实现关系：** DriverExtensionContext extends ExtensionContext

**起始版本：** 23

<!--Device-unnamed-declare class DriverExtensionContext--><!--Device-unnamed-declare class DriverExtensionContext-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## updateDriverState

```TypeScript
updateDriverState(): void
```

驱动状态上报。预留接口，暂不提供具体功能。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionContext-updateDriverState(): void--><!--Device-DriverExtensionContext-updateDriverState(): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

