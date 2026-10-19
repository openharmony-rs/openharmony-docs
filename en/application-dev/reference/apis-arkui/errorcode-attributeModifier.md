# Error Codes for Dynamic Attribute Configuration
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangjunman1-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e905bb0bc26b0b10f58e2efc6bc5284ead61d838 translatedAt=2026-08-29T09:18:04.345Z pushedAt=2026-08-31T01:51:03.510Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 100201 attributeModifier Does Not Support Some APIs

**Error Message**

Something not supported in attributeModifier scenario.

**Description**

This error code is reported when some APIs do not support the configuration of [attributeModifier](./arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier). For details, see [attributeModifier Support for Attributes and Events](../../ui/arkts-user-defined-extension-attributeModifier.md#attributemodifier-support-for-attributes-and-events).

**Possible Causes**

The dynamic attribute setting mechanism of **attributeModifier** does not support some APIs, so these APIs cannot set attributes through this mechanism.

**Solution**

Stop using the unsupported APIs. For details, see [JS Crash Occurs When AttributeModifier Is Used to Set Dynamic Attributes for a Component](../../ui/arkts-attribute-modifier-faq.md#js-crash-occurs-when-attributemodifier-is-used-to-set-dynamic-attributes-for-a-component).

