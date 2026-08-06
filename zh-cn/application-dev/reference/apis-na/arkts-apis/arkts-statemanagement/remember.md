# stateManagement/remember

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [rememberVariable](remember-remembervariable-f.md#remembervariable) | 创建状态变量。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [MutableVariable](remember-mutablevariable-i.md) | rememberVariable创建的状态变量类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RememberInitialType](arkts-na-rememberinitialtype-t.md) | 状态变量初始值入参类型。基础类型使用类型T直接传入； 复杂类型（interface、class和包含Array、Map、Set和Date的内置类型）使用回调（() => T）初始化能避免重复创建实例，性能更高。 |

