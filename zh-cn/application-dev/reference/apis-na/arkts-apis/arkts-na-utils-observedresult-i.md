# ObservedResult

对象是否可被观察的结果。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export interface ObservedResult--><!--Device-unnamed-export interface ObservedResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoratorInfo

```TypeScript
decoratorInfo: DecoratorInfo[]
```

对象可被观察时，数组中内容为对象关联的装饰器和组件信息。对象不可被观察时，此数组为空。

**类型：** [DecoratorInfo](arkts-na-utils-decoratorinfo-i.md)[]

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedResult-decoratorInfo: DecoratorInfo[]--><!--Device-ObservedResult-decoratorInfo: DecoratorInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isObserved

```TypeScript
isObserved: boolean
```

对象是否可被观察。 true：表示是可被观察对象。 false：表示不是可被观察对象。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedResult-isObserved: boolean--><!--Device-ObservedResult-isObserved: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: string
```

对象是否可被观察的原因。 不可被观察原因：对象本身是不可被观察的。 可被观察原因或使用场景： 1. 对象被@Observed装饰器装饰。 2. 对象被@ObservedV2和@Trace装饰。 3. 对象为被V1装饰器装饰或被makeObserved方法转换的interface字面量。 4. 对象为被V1/V2装饰器装饰或被makeObserved方法转换的Array/Map/Set/Date类型。 5. 对象被@Observed装饰器装饰，但未使用在UI上。 6. 对象被@ObservedV2和@Trace装饰，但未使用在UI上。 7. 对象为被V1装饰器装饰或被makeObserved方法转换的interface字面量，但未用在UI上。 8. 对象为被V1/V2装饰器装饰或被makeObserved方法转换的Array/Map/Set/Date类型，但未用在UI上。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ObservedResult-reason: string--><!--Device-ObservedResult-reason: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

