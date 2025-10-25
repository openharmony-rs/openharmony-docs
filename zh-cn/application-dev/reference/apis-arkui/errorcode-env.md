# 环境变量错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

## 140000 \@Env非法入参

**错误信息**

Invalid key for @Env

**错误描述**

[\@Env](./arkui-ts/ts-env-system-property.md#env)非法入参。

**可能原因**

\@Env入参非法。\@Env仅支持[SystemProperties](./arkui-ts/ts-env-system-property.md#systemproperties)类型参数，详情见[\@Env支持参数](../../ui/arkts-env-system-property.md#env支持参数)。

**处理步骤**

确保\@Env参数类型为[SystemProperties](./arkui-ts/ts-env-system-property.md#systemproperties)，详情见[\@Env支持开发指南](../../ui/arkts-env-system-property.md)。

