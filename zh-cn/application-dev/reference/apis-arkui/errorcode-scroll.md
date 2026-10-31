# 滚动类组件错误码

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 100004 控制器未绑定组件

**错误信息**

Controller not bound to component.

**错误描述**

控制器未绑定组件，通过控制器调用接口时，系统会产生此错误码。该错误码为string类型。

**可能原因**

控制器未绑定组件，通过控制器调用接口。

**处理步骤**

请检查控制器是否绑定了组件，或者控制器绑定的组件是否已经被释放。

## 100031 占位模板注册被拒绝

**错误信息**

Registration rejected: the builder is not marked with @Builder({ isPlaceholder: true }). The ID is not registered.

**错误描述**

调用[PlaceholderRegister](./arkts-apis-placeholderregister.md#placeholderregister)的[register](./arkts-apis-placeholderregister.md#register)接口注册滚动占位模板时，传入的builder未在编译期标记为`@Builder({ isPlaceholder: true })`，系统会产生此错误码，该id不会注册成功。

**可能原因**

传入的builder不是`@Builder({ isPlaceholder: true })`函数，或通过绕过编译期类型检查的动态方式传入了未标记的builder。

**处理步骤**

请确认占位模板为全局、无参、只读静态渲染的`@Builder({ isPlaceholder: true })`函数，并经wrapBuilder包装后传入register接口。

