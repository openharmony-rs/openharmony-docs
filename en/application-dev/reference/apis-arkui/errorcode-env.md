# Environment Variable Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

> **NOTE:**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 140000 Invalid \@Env Input Parameter

**Error Message**

Invalid key for @Env

**Description**

This error code is reported when an invalid parameter is passed to [\@Env](./arkui-ts/ts-env-system-property.md#env).

**Possible Causes**

The parameter provided to \@Env is invalid. \@Env supports the parameter of the [SystemProperties](./arkui-ts/ts-env-system-property.md#systemproperties) \| [SystemEnvKey\<T\>](./arkui-ts/ts-env-system-property.md#systemenvkeyt) type. For details, see [Supported Parameters](../../ui/arkts-env-system-property.md#supported-parameters).

**Solution**

Ensure that the type of the parameter provided to \@Env is [SystemProperties](./arkui-ts/ts-env-system-property.md#systemproperties) \| [SystemEnvKey\<T\>](./arkui-ts/ts-env-system-property.md#systemenvkeyt). For details, see [\@Env: Environment Variable](../../ui/arkts-env-system-property.md)

<!--no_check-->