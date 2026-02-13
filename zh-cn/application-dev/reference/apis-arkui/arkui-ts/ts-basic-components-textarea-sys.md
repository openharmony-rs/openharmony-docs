# TextArea (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

多行文本输入框组件。

> **说明：**
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[TextArea](ts-basic-components-textarea.md)。

## voiceButton<sup>23+</sup>

voiceButton(options: Optional\<VoiceButtonOptions\>)

设置语音按钮选项。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ----- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt12)<[VoiceButtonOptions](./ts-text-common-sys.md#voicebuttonoptions23)> | 是  | 语音按钮选项参数。 |


## 示例

### 示例1 (设置语音按钮)

该示例通过配置voiceButton接口，为输入框启用语音输入按钮。

从API version 23开始，新增[voiceButton](#voicebutton23)接口。

```ts
// xxx.ets
@Entry
@Component
struct TextAreaExample {

  build() {
    Column() {
      TextArea().voiceButton({enabled: true})
    }
  }
}
```