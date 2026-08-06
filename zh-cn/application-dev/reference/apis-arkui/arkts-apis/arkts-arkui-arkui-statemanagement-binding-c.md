# Binding

只读数据绑定的泛型类，可以绑定任意类型的数据。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-unnamed-export declare class Binding<T>--><!--Device-unnamed-export declare class Binding<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
get value(): T
```

提供get访问器，用于获取绑定的值。

**类型：** T

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Binding-get value(): T--><!--Device-Binding-get value(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

