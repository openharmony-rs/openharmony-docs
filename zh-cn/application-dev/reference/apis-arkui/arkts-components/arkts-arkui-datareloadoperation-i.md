# DataReloadOperation

重载所有数据操作，并配置是否允许在更新过程中复用旧的子组件。当onDatasetChange含有DataOperationType.RELOAD操作时，其余操作全部失效，框架会自己调用keyGenerator进行键值比对。配置允许在更新过程中复用旧的子组件，并和[@Reusable](../../../ui/state-management/arkts-reusable.md)/ [@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md)配合使用时，优先使用复用池中的组件，若复用池中无可复用的组件，而LazyForEach的旧子组件中 有可复用的组件，该组件将被回收，并复用为新的子组件。当LazyForEach的旧子组件中也没有可复用的组件时，将创建新的子组件。配置允许在更新过程中复用旧的子组件，未使用@Reusable/@ReusableV2时，键值没有变化的数据项会使用原先的子组件，键值发生变化的会重建子组件。配置不允许在更新过程中复用旧的子组件，键值没有变化的数据项会使用原先的子组件，键值发生变化的数据项，若使用了@Reusable/@ReusableV2且复用池中有可用的组件，将复用旧组件，否则将创建新的子组件。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## reuseImmediately

```TypeScript
reuseImmediately?: boolean
```

是否允许在更新过程中复用旧的子组件。true：允许在更新过程中复用旧的子组件。false：不允许在更新过程中复用旧的子组件。默认值：false当值为undefined或null时，取默认值。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: DataOperationType.RELOAD
```

数据全部重载类型。

**类型：** [DataOperationType.RELOAD](arkts-arkui-dataoperationtype-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
