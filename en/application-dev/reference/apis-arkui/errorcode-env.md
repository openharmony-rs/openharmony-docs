# Environment Variable Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=cba601fed1dc0fc6124c12259c5ea80f13701d69 translatedAt=2026-08-29T09:19:45.877Z pushedAt=2026-08-31T03:15:30.768Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 140000 Invalid Key for @Env

**Error Message**

Invalid key for @Env

**Description**

This error code is reported when there is an invalid key for [@Env](./arkui-ts/ts-env-system-property.md#env).

**Possible Causes**

A key not supported by **@Env** is used. **@Env** accepts only the predefined [SystemProperties](./arkui-ts/ts-env-system-property.md#systemproperties) and [SystemEnvKey\<T\>](./arkui-ts/ts-env-system-property.md#systemenvkeyt) type parameters. Passing a key outside the supported range triggers this error. For details, see [Supported Parameters](../../ui/arkts-env-system-property.md#supported-parameters).

**Solution**

Ensure that the type of the parameter supported by **@Env** is [SystemProperties](./arkui-ts/ts-env-system-property.md#systemproperties) \| [SystemEnvKey\<T\>](./arkui-ts/ts-env-system-property.md#systemenvkeyt). For details, see [@Env: Environment Variable](../../ui/arkts-env-system-property.md).

<!--no_check-->