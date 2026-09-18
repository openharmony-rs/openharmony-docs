# PublishFormErrorCode (System API)

Enumerates the result codes that may be used for the operation of adding a widget to the home screen.

**Since:** 12

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## SUCCESS

```TypeScript
SUCCESS = 0
```

The widget is added to the home screen.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## NO_SPACE

```TypeScript
NO_SPACE = 1
```

There is no space for adding widgets.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## PARAM_ERROR

```TypeScript
PARAM_ERROR = 2
```

Parameter check fails.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## INTERNAL_ERROR

```TypeScript
INTERNAL_ERROR = 3
```

An internal error occurs during widget processing.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## NOT_SUPPORT

```TypeScript
NOT_SUPPORT = 4
```

Indicates that the host does not support the form.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## HOST_FORM_LIMIT

```TypeScript
HOST_FORM_LIMIT = 5
```

Indicates that the number of forms added to the host exceeds the upper limit.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
