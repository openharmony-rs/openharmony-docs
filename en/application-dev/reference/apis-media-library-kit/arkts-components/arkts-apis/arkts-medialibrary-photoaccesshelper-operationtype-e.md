# OperationType

Enumerates the predicates.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## EQUAL_TO

```TypeScript
EQUAL_TO = 1
```

Checks for equality, using the first element of the **value** array to match the predicate. If the array is longer, only the first element is considered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOT_EQUAL_TO

```TypeScript
NOT_EQUAL_TO = 2
```

Checks for inequality, using the first element of the **value** array to match the predicate. If the array is longer, only the first element is considered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## GREATER_THAN

```TypeScript
GREATER_THAN = 3
```

Checks whether the value is greater than the predicate, using the first element of the **value** array to match the predicate. If the array is longer, only the first element is considered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LESS_THAN

```TypeScript
LESS_THAN = 4
```

Checks whether the value is less than the predicate, using the first element of the **value** array to match the predicate. If the array is longer, only the first element is considered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## GREATER_THAN_OR_EQUAL_TO

```TypeScript
GREATER_THAN_OR_EQUAL_TO = 5
```

Checks whether the value is greater than or equal to the predicate, using the first element of the **value** array to match the predicate. If the array is longer, only the first element is considered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## LESS_THAN_OR_EQUAL_TO

```TypeScript
LESS_THAN_OR_EQUAL_TO = 6
```

Checks whether the value is less than or equal to the predicate, using the first element of the **value** array to match the predicate. If the array is longer, only the first element is considered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## AND

```TypeScript
AND = 7
```

Logical 'AND', similar to 'and' in database queries. No **field** or **value** is needed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## OR

```TypeScript
OR = 8
```

Logical 'OR', similar to 'or' in database queries. No **field** or **value** is needed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## IN

```TypeScript
IN = 9
```

Matches fields within a specified range, with a maximum value length of 10.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOT_IN

```TypeScript
NOT_IN = 10
```

Matches fields outside a specified range, with a maximum value length of 10.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BEGIN_WRAP

```TypeScript
BEGIN_WRAP = 11
```

Adds a left parenthesis to the predicate, similar to "(" in database queries. It must be used with a right parenthesis. No **field** or **value** is needed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## END_WRAP

```TypeScript
END_WRAP = 12
```

Adds a right parenthesis to the predicate, similar to ")" in database queries. It must be used with a left parenthesis. No **field** or **value** is needed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BETWEEN

```TypeScript
BETWEEN = 13
```

Matches fields within a specified range,

including both endpoints (closed interval). It uses the first two elements of the **value** array, where the first element is the lower boundary and the second is the upper boundary. For example, in the array [1, 2, 3, 4], the first two elements are used, with 1 as the lower boundary and 2 as the upper boundary.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## NOT_BETWEEN

```TypeScript
NOT_BETWEEN = 14
```

Matches fields outside a specified range,

excluding both endpoints (open interval). It uses the first two elements of the **value** array, where the first element is the lower boundary and the second is the upper boundary. For example, in the array [1, 2, 3, 4], the first two elements are used, with 1 as the lower boundary and 2 as the upper boundary.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
