# SendableContext

SendableContext符合[Sendable协议](../../../arkts-utils/arkts-sendable.md#sendable协议)， 可以与Context对象相互转换，用于ArkTS并发实例间（包括主线程、TaskPool&Worker工作线程）的数据传递。

**继承/实现关系：** SendableContext extends lang.ISendable

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
