# Environment Variable Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=535c657bccd3aaa06defedade06b3c64137965be translatedAt=2026-10-15T10:43:24.950Z pushedAt=2026-10-16T02:55:30.994Z -->

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