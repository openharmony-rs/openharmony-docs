# ReadonlySet

ReadonlySet的实现。

**继承/实现关系：** ReadonlySet extends Iterable<T>

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface ReadonlySet--><!--Device-unnamed-export interface ReadonlySet-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## has

```TypeScript
has(value: T): boolean
```

检查某个值是否在该Set中。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReadonlySet-has(value: T): boolean--><!--Device-ReadonlySet-has(value: T): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 待在该Set中查找的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果该值在Set中则返回true。 |

