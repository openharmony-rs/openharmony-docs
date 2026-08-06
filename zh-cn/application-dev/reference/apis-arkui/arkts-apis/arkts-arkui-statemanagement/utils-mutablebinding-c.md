# MutableBinding

可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class MutableBinding<T>--><!--Device-unnamed-export declare class MutableBinding<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
set value(newValue: T)
```

提供set访问器，用于设置当前绑定值。构造MutableBinding类实例时必须提供set访问器，否则会触发运行时错误。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MutableBinding-set value(newValue: T)--><!--Device-MutableBinding-set value(newValue: T)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

