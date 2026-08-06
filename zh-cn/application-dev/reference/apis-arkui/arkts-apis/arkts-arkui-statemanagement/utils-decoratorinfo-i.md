# DecoratorInfo

可被观察对象关联的装饰器和组件信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export interface DecoratorInfo--><!--Device-unnamed-export interface DecoratorInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoratorName

```TypeScript
decoratorName: string
```

当对象被\_\_\_MD\_LINK\_DESC\_USD\_7\_\_\_装饰时，值为对象关联的装饰器名称。 当对象属性使用\_\_\_MD\_LINK\_DESC\_USD\_8\_\_\_时，值为：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 当对象属性使用\_\_\_MD\_LINK\_DESC\_USD\_9\_\_\_时，值为：\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_。 当对象经过[makeObserved]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_转换时，值为： \_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_。 当对象为被V1装饰器装饰的built-in类型时，值为对象关联的装饰器名称。 当对象为被V1装饰器装饰的interface字面量时，值为对象关联的装饰器名称。 当对象被@Observed装饰且使用在V2组件中时，值为：\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_。 当对象为被V1装饰器装饰的built-in类型且使用在V2组件中时，值为：\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_。 当对象为被V1装饰器装饰的interface字面量且使用在V2组件中时，值为：\_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_。 当对象为被V2装饰器装饰的built-in类型时，值为：\_\_\_INLINE\_CODE\_DESC\_USD\_6\_\_\_。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecoratorInfo-decoratorName: string--><!--Device-DecoratorInfo-decoratorName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dependentInfo

```TypeScript
dependentInfo: ElementInfo[]
```

使用该可观察对象的组件信息。若对象没有用在任何UI上，则返回空数组。

**类型：** ElementInfo[]

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecoratorInfo-dependentInfo: ElementInfo[]--><!--Device-DecoratorInfo-dependentInfo: ElementInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## owningComponentId

```TypeScript
owningComponentId: int
```

在V1组件中被状态管理V1装饰器装饰的@Observed装饰的对象、interface字面量和built-in类型对象返回V1组件ID。 其余情况返回-1。

**类型：** int

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecoratorInfo-owningComponentId: int--><!--Device-DecoratorInfo-owningComponentId: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## owningComponentOrClassName

```TypeScript
owningComponentOrClassName: string
```

在V1组件中被状态管理V1装饰器装饰的@Observed装饰的对象、interface字面量和built-in类型对象返回V1组件名称。 使用@Track装饰器、@Trace装饰器时返回对象名称。 使用V2装饰器装饰或makeObserved转换的built-in对象时，返回对象名称。 使用makeObserved转换的interface字面量时，返回字面量的定义名称。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecoratorInfo-owningComponentOrClassName: string--><!--Device-DecoratorInfo-owningComponentOrClassName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stateVariableName

```TypeScript
stateVariableName: string
```

被装饰器装饰的属性名称。 在V1组件中被状态管理V1装饰器装饰的@Observed装饰的对象、interface字面量和built-in类型对象返回V1装饰器的名称。 使用@Track装饰器、@Trace装饰器时返回属性名。 使用V2装饰器装饰或makeObserved转换的built-in对象时，返回可观测属性的名称。常见的框架内置可观察属性见下表。 makeObserved转换的interface字面量返回\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecoratorInfo-stateVariableName: string--><!--Device-DecoratorInfo-stateVariableName: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

