# OperationType

表示各类谓词的枚举。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## EQUAL_TO

```TypeScript
EQUAL_TO = 1
```

等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOT_EQUAL_TO

```TypeScript
NOT_EQUAL_TO = 2
```

不等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## GREATER_THAN

```TypeScript
GREATER_THAN = 3
```

大于，取value数组的第一个元素与谓词匹配。 超出长度取第1个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LESS_THAN

```TypeScript
LESS_THAN = 4
```

小于，取value数组的第一个元素与谓词匹配。超出长度取第1个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## GREATER_THAN_OR_EQUAL_TO

```TypeScript
GREATER_THAN_OR_EQUAL_TO = 5
```

大于等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LESS_THAN_OR_EQUAL_TO

```TypeScript
LESS_THAN_OR_EQUAL_TO = 6
```

小于等于，取value数组的第一个元素与谓词匹配。超出长度取第1个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## AND

```TypeScript
AND = 7
```

逻辑'与'，相当于数据库查询语句的'and'。无需传入field和value。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## OR

```TypeScript
OR = 8
```

逻辑'或'，相当于数据库查询语句的'or'。无需传入field和value。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## IN

```TypeScript
IN = 9
```

匹配在指定范围内的字段，value长度限制10个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOT_IN

```TypeScript
NOT_IN = 10
```

匹配不在指定范围内的字段，value长度限制10个。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BEGIN_WRAP

```TypeScript
BEGIN_WRAP = 11
```

用于向谓词添加英文左括号，相当于数据库查询语句的"("，必须和英文右括号一起使用。无需传入field和value。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## END_WRAP

```TypeScript
END_WRAP = 12
```

用于向谓词添加英文右括号，相当于数据库查询语句的")"，必须和英文左括号一起使用。无需传入field和value。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BETWEEN

```TypeScript
BETWEEN = 13
```

匹配指定范围内的字段。包含两端边界值，为左闭右闭区间。取value数组的前两个元素与谓词匹配，超出长度取前2个，分别表示左右边界。例如：[1, 2, 3, 4]中取前两个，1表示左边界，2表示右边界。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOT_BETWEEN

```TypeScript
NOT_BETWEEN = 14
```

匹配超出指定范围内的字段。不包含两端边界值，为左开右开区间。取value数组的前两个元素与谓词匹配，超出长度取前2个，分别表示左右边界。例如：[1, 2, 3, 4]中取前两个，1表示左边界，2表示右边界。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
