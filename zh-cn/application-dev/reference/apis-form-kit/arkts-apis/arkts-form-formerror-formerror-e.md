# FormError

枚举，卡片错误码。

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_COMMON

```TypeScript
ERR_COMMON = 1
```

A common internal error occurs during form processing.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_PERMISSION_DENY

```TypeScript
ERR_PERMISSION_DENY = 2
```

The application does not have permission to use forms. Ensure that the application is granted with the ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED permissions.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_GET_INFO_FAILED

```TypeScript
ERR_GET_INFO_FAILED = 4
```

Failed to obtain the configuration information about the form specified by the request parameters. Ensure that the parameters of the form to be added are consistent with those provided by the form provider.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_GET_BUNDLE_FAILED

```TypeScript
ERR_GET_BUNDLE_FAILED = 5
```

Failed to obtain the bundle to which the form belongs based on the request parameters. Ensure that the bundle to which the form to be added belongs is available.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_GET_LAYOUT_FAILED

```TypeScript
ERR_GET_LAYOUT_FAILED = 6
```

Failed to initialize the form layout based on the request parameters. Ensure that the grid style of the form is supported by the form provider.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_ADD_INVALID_PARAM

```TypeScript
ERR_ADD_INVALID_PARAM = 7
```

Invalid input parameter during form operation. Ensure that all input parameters are valid.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_CFG_NOT_MATCH_ID

```TypeScript
ERR_CFG_NOT_MATCH_ID = 8
```

The form configuration to be obtained using an existing form ID is different from that obtained for the first time.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_NOT_EXIST_ID

```TypeScript
ERR_NOT_EXIST_ID = 9
```

The ID of the form to be operated does not exist in the Form Manager Service.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_BIND_PROVIDER_FAILED

```TypeScript
ERR_BIND_PROVIDER_FAILED = 10
```

Failed to bind the Form Manager Service to the provider service.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_MAX_SYSTEM_FORMS

```TypeScript
ERR_MAX_SYSTEM_FORMS = 11
```

The total number of added forms exceeds the maximum allowed by the system.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_MAX_INSTANCES_PER_FORM

```TypeScript
ERR_MAX_INSTANCES_PER_FORM = 12
```

The number of form instances generated using the same form configuration exceeds the maximum allowed by the system.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_OPERATION_FORM_NOT_SELF

```TypeScript
ERR_OPERATION_FORM_NOT_SELF = 13
```

The form being requested was added by other applications and cannot be operated by the current application.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_PROVIDER_DEL_FAIL

```TypeScript
ERR_PROVIDER_DEL_FAIL = 14
```

The Form Manager Service failed to instruct the form provider to delete the form.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_MAX_FORMS_PER_CLIENT

```TypeScript
ERR_MAX_FORMS_PER_CLIENT = 15
```

The total number of added forms exceeds the maximum per client.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_MAX_SYSTEM_TEMP_FORMS

```TypeScript
ERR_MAX_SYSTEM_TEMP_FORMS = 16
```

The total number of added temp forms exceeds the maximum in system.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_FORM_NO_SUCH_MODULE

```TypeScript
ERR_FORM_NO_SUCH_MODULE = 17
```

The module can not be find in system.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_FORM_NO_SUCH_ABILITY

```TypeScript
ERR_FORM_NO_SUCH_ABILITY = 18
```

The ability can not be find in system.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_FORM_NO_SUCH_DIMENSION

```TypeScript
ERR_FORM_NO_SUCH_DIMENSION = 19
```

The dimension is not exist in the form.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_FORM_FA_NOT_INSTALLED

```TypeScript
ERR_FORM_FA_NOT_INSTALLED = 20
```

The ability is not installed.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_SYSTEM_RESPONSES_FAILED

```TypeScript
ERR_SYSTEM_RESPONSES_FAILED = 30
```

Failed to obtain the RPC object of the Form Manager Service because the service is not started.Please try again after the service is started.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_FORM_DUPLICATE_ADDED

```TypeScript
ERR_FORM_DUPLICATE_ADDED = 31
```

Failed to obtain the form requested by the client because another form with the same form ID is in use. Forms in use cannot have the same ID. To obtain and display a form that has the same configuration as an in-use form in the same application, you are advised to set the form ID to 0 in the request parameters.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form

## ERR_IN_RECOVERY

```TypeScript
ERR_IN_RECOVERY = 36
```

The form is being restored. Perform operations on the form only after the restoration is complete.

**起始版本：** 8

**系统能力：** SystemCapability.Ability.Form
