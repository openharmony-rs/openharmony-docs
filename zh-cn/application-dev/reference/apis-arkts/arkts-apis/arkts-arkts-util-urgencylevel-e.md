# UrgencyLevel

```TypeScript
enum UrgencyLevel
```

枚举，提示触发GC的紧急程度。

**起始版本：** 26.1.0

<!--Device-util-enum UrgencyLevel--><!--Device-util-enum UrgencyLevel-End-->

**系统能力：** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 2
```

紧急程度高，GC触发阈值低。适用于应用的ArkTS内存压力已经非常高，开发者期望系统尽可能快地触发GC去回收内存的场景

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UrgencyLevel-HIGH = 2--><!--Device-UrgencyLevel-HIGH = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 0
```

紧急程度低，GC触发阈值较高但仍低于正常的GC触发阈值。适用于开发者期望主动触发GC去回收已死亡的对象但是应用的ArkTS内存压力仍然可控的场景。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UrgencyLevel-LOW = 0--><!--Device-UrgencyLevel-LOW = 0-End-->

**系统能力：** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

紧急程度中等，GC触发阈值介于LOW和HIGH之间。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UrgencyLevel-MEDIUM = 1--><!--Device-UrgencyLevel-MEDIUM = 1-End-->

**系统能力：** SystemCapability.Utils.Lang
