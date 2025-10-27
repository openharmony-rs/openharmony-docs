# 应用内拉起卡片管理加桌
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @Brilliantry_Rui-->

从API version 18开始，Form Kit提供在应用内将ArkTS卡片添加到桌面的能力，以方便用户后续便捷查看信息或快速进入应用。

## 开发步骤
下面给出示例，实现如下功能：在应用内点击“添加卡片到桌面”按钮，拉起卡片管理页面。用户可在卡片管理页面，点击“添加至桌面”按钮，此时在桌面即可看到新添加的卡片。
1. [创建卡片](./arkts-ui-widget-creation.md)。
2. 通过[openFormManager](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovideropenformmanager18)方法在应用内添加拉起卡片管理页面入口。

<!-- @[FormManagerDemo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormManagerDemo/entry/src/main/ets/pages/Index.ets) -->

资源文件如下：
```json
// entry/src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "open_form_manager_button",
      "value": "添加应用卡片到桌面"
    }
  ]
}
```

3. 用户可在卡片管理页面，点击“添加至桌面”，此时在桌面即可看到新添加的卡片。结果示例如下。<br>
![WidgetPrinciple](figures/应用内加卡.gif)
