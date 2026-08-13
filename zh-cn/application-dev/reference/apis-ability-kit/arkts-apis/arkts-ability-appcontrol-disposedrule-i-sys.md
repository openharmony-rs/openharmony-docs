# DisposedRule（系统接口）

标识拦截规则。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appControl-export interface DisposedRule--><!--Device-appControl-export interface DisposedRule-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## componentType

```TypeScript
componentType: ComponentType
```

拦截时将提升的能力的类型。

**类型：** ComponentType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisposedRule-componentType: ComponentType--><!--Device-DisposedRule-componentType: ComponentType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## controlType

```TypeScript
controlType: ControlType
```

拦截指定应用程序的不同策略。

**类型：** [ControlType](arkts-ability-appcontrol-controltype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisposedRule-controlType: ControlType--><!--Device-DisposedRule-controlType: ControlType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## disposedType

```TypeScript
disposedType: DisposedType
```

对应用的拦截规则。

**类型：** [DisposedType](arkts-ability-appcontrol-disposedtype-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisposedRule-disposedType: DisposedType--><!--Device-DisposedRule-disposedType: DisposedType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## elementList

```TypeScript
elementList: Array<ElementName>
```

拦截指定应用程序能力的列表。

**类型：** Array&lt;[ElementName](arkts-ability-elementname-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisposedRule-elementList: Array<ElementName>--><!--Device-DisposedRule-elementList: Array<ElementName>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## priority

```TypeScript
priority: int
```

拦截规则的优先级，用于规则列表查询结果排序。取值为整数，数值越小，优先级越高，排序越靠前。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisposedRule-priority: int--><!--Device-DisposedRule-priority: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## want

```TypeScript
want: Want
```

指定应用被拦截时，跳转到的页面。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisposedRule-want: Want--><!--Device-DisposedRule-want: Want-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

