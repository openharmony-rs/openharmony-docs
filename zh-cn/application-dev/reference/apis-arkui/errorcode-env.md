# 环境变量错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考通用错误码。

## 140000 @Env无效键

**错误信息**

Invalid key for @Env

**错误描述**

@Env无效键。

**可能原因**

使用了@Env不支持的键。@Env仅接受预定义的SystemProperties和SystemEnvKey\<T\>类型参数，传入不在支持范围内的键将触发此错误。详情见@Env支持参数。

**处理步骤**

确保@Env参数类型为SystemProperties \| SystemEnvKey\<T\>，详情见@Env支持开发指南。