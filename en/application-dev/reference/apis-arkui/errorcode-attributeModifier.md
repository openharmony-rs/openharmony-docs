# Error Codes for Dynamic Attribute Configuration
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangjunman1-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100201 attributeModifier Not Supported by Some APIs

**Error Message**

Something not supported in attributeModifier scenario.

**Description**

This error code is reported when some APIs do not support the configuration of [attributeModifier](./arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier). For details, see [attributeModifier Support for Attributes and Events](../../ui/arkts-user-defined-extension-attributeModifier.md#attributemodifier-support-for-attributes-and-events).

**Possible Causes**

Some APIs do not support the configuration of **attributeModifier**.

**Solution**

Stop using these APIs based on the error code information. For details, see [Using AttributeModifier to Set Component Dynamic Attributes Causes JS Crash](../../ui/arkts-attribute-modifier-faq.md#using-attributemodifier-to-set-component-dynamic-attributes-causes-js-crash).
