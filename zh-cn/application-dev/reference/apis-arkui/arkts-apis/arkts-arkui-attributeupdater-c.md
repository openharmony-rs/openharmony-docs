# AttributeUpdater

为[AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)的实现类，开发者需要自定义class继承AttributeUpdater。其中C代表组件的构造函数类型，比如Text组件的TextInterface，Image组件的ImageInterface等，仅在使用updateConstructorParams时才需要传递C类型。

**继承/实现关系：** AttributeUpdater implements [AttributeModifier<T>](AttributeModifier<T>)

**起始版本：** 12

<!--Device-unnamed-export declare class AttributeUpdater<T, C = Initializer<T>> implements AttributeModifier<T>--><!--Device-unnamed-export declare class AttributeUpdater<T, C = Initializer<T>> implements AttributeModifier<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="applynormalattribute"></a>
## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: T): void
```

定义正常态更新属性函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AttributeUpdater-applyNormalAttribute?(instance: T): void--><!--Device-AttributeUpdater-applyNormalAttribute?(instance: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如Button组件的ButtonAttribute，Text组件的TextAttribute等。 |

<a id="initializemodifier"></a>
## initializeModifier

```TypeScript
initializeModifier(instance: T): void
```

AttributeUpdater首次设置给组件时提供的样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AttributeUpdater-initializeModifier(instance: T): void--><!--Device-AttributeUpdater-initializeModifier(instance: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如Button组件的ButtonAttribute，Text组件的TextAttribute等。 |

<a id="oncomponentchanged"></a>
## onComponentChanged

```TypeScript
onComponentChanged(component: T): void
```

绑定相同的自定义的Modifier对象，组件发生切换时，通过该接口通知到应用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AttributeUpdater-onComponentChanged(component: T): void--><!--Device-AttributeUpdater-onComponentChanged(component: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如Button组件的ButtonAttribute，Text组件的TextAttribute等。 |

## attribute

```TypeScript
get attribute(): T | undefined
```

获取AttributeUpdater中组件对应的属性类实例，通过该实例实现属性直通更新的功能。

**类型：** T

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AttributeUpdater-get attribute(): T | undefined--><!--Device-AttributeUpdater-get attribute(): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateConstructorParams

```TypeScript
updateConstructorParams: C
```

用于更改组件的构造函数入参。C代表组件的构造函数类型，比如Text组件的TextInterface，Image组件的ImageInterface等。

**类型：** C

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AttributeUpdater-updateConstructorParams: C--><!--Device-AttributeUpdater-updateConstructorParams: C-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

