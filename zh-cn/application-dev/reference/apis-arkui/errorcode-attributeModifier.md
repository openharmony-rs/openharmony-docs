# 动态属性设置错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangjunman1-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 100201 attributeModifier不支持部分接口的使用

**错误信息**

Something not supported in attributeModifier scenario.

**错误描述**

部分接口不支持通过[attributeModifier](./arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)设置，具体请参考[属性或事件对attributeModifier的支持情况](../../ui/arkts-user-defined-extension-attributeModifier.md#属性或事件对attributemodifier的支持情况)。

**可能原因**

部分接口不支持通过attributeModifier设置。

**处理步骤**

根据错误码对应的具体信息，停止使用该部分接口，请参考[用attributemodifier设置组件动态属性出现jscrash](../../ui/arkts-attribute-modifier-faq.md#使用attributemodifier设置组件动态属性出现jscrash)。

