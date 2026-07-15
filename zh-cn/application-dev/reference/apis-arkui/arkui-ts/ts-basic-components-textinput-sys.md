# TextInput (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

单行文本输入框组件，用于接收用户输入的单行文本内容，支持多种输入类型（如密码、语音等），可应用于表单填写、搜索框、登录注册等场景，帮助开发者快速构建用户交互界面。

> **说明：**
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[TextInput](ts-basic-components-textinput.md)。

## InputType枚举说明

单行文本输入框类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                                 | 值 | 说明                                       |
| ---------------------------------- | --- | ---------------------------------------- |
| SCREEN_LOCK_PASSWORD<sup>11+</sup> | 9 | 锁屏应用密码输入模式。支持输入数字、字母、下划线、空格、特殊字符。密码显示小眼睛图标并且默认会将文字变成圆点，从API version 12开始，Wearable设备上输入文字直接显示为圆点。密码输入模式不支持下划线样式。 <br>**系统接口：** 此接口为系统接口。<br>**模型约束：** 此接口仅可在Stage模型下使用。 |
## voiceButton<sup>23+</sup>

voiceButton(options: Optional\<VoiceButtonOptions\>)

设置语音按钮选项，启用后将在输入框中显示语音输入按钮，用户可通过语音进行输入。

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ----- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[VoiceButtonOptions](./ts-text-common-sys.md#voicebuttonoptions23)\> | 是  | 语音按钮配置选项，用于控制语音输入按钮的启用状态和行为。当需要在TextInput组件中启用语音输入功能时使用此参数，具体配置项参见VoiceButtonOptions类型定义。 |


## 示例

### 示例1 (设置语音按钮)

该示例通过配置voiceButton接口，为输入框启用语音输入按钮。

从API version 23开始，新增[voiceButton](#voicebutton23)接口。

```ts
// xxx.ets
@Entry
@Component
struct TextInputExample {

  build() {
    Column() {
      TextInput().voiceButton({enabled: true})
    }
  }
}
```