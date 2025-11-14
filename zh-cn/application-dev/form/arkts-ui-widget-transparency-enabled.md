# 透明卡片开发指导
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @liujing-->
<!--Adviser: @Brilliantry_Rui-->
从API version 20开始，Form Kit提供应用开发者实现卡片背板元素透明显示的能力，满足更丰富的UI设计以及美观诉求。

## 开发步骤
卡片创建完成后，需要完成背板透明卡片配置，并接入背板透明卡片开发能力，其他开发流程与普通卡片一致，具体步骤参考如下。

### 透明卡片配置
在form_config.json配置文件中，透明卡片必须配置transparencyEnabled字段。transparencyEnabled字段支持true或者false，具体参考[配置文件字段说明](./arkts-ui-widget-configuration.md)

    ```json
    // entry/src/main/resources/base/profile/form_config.json

    {
      "forms": [
        {
            "name": "widget",
            "displayName": "$string:widget_display_name",
            "description": "$string:widget_desc",
            "src": "./ets/widget/pages/WidgetCard.ets",
            "uiSyntax": "arkts",
            "window": {
                "designWidth": 720,
                "autoDesignWidth": true
            },
            "colorMode": "auto",
            "isDynamic": true,
            "isDefault": true,
            "updateEnabled": false,
            "scheduledUpdateTime": "10:30",
            "updateDuration": 1,
            "defaultDimension": "2*2",
            "transparencyEnabled": true,
            "supportDimensions": [
                "2*2"
            ]
        },
      ]
    }
    ```

### 透明卡片开放能力申请
因为透明卡片仅使用于符合UI规范以及声明使用的场景，不进行对用户隐藏卡片显示或者功能按钮的恶意设计，所以需要开发者申请上架开放能力。

因此在应用调试或发布时，必须使用[手动签名](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-signing#section297715173233)，并在手动签名[申请Profile](https://developer.huawei.com/consumer/cn/doc/app/agc-help-debug-profile-0000002248181278)过程中[创建HarmonyOS应用](https://developer.huawei.com/consumer/cn/doc/app/agc-help-create-app-0000002247955506)，创建应用时参考如下指导为应用接入开放能力。

1.在“开放能力接入”页面，点击背板透明卡片对应的申请按钮。

2.在“新建业务申请”窗口填写申请信息，然后点击“提交”。申请原因：必填，不超过256个字符。上传附件：必填，仅可上传1个附件，大小不超过500MB。支持文本、表格、图片、视频、压缩包格式。

3.返回“开放能力接入”页面，原“申请”按钮变为“申请中”，1-3个工作日反馈申请结果。

4.申请审批通过后，互动中心会发送通知给您，同时“申请中”按钮会变为置灰显示的“申请”。

5.能力申请通过后，勾选背板透明卡片的能力开关，点击右上角“保存”。至此，您的应用已成功接入开放能力。