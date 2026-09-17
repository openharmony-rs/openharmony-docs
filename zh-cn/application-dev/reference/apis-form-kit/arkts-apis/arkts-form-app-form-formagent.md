# @ohos.app.form.formAgent(FormAgent)

FormAgent模块提供了卡片代理相关接口的能力，目前仅包括请求发布卡片。适用于系统应用需要将卡片发布到使用方（如桌面）的场景，能够帮助系统应用便捷地请求发布卡片，简化卡片发布流程。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [requestPublishForm](arkts-form-formagent-requestpublishform-f-sys.md) | 请求发布一张卡片到使用方，使用callback异步回调。使用方通常为桌面。适用于系统应用需要主动将卡片添加到桌面的场景。 |
| [requestPublishForm](arkts-form-formagent-requestpublishform-f-sys.md) | 请求发布一张卡片到使用方，使用Promise异步回调。使用方通常为桌面。适用于系统应用需要主动将卡片添加到桌面的场景。 |
| [updateFormCrossBundle](arkts-form-formagent-updateformcrossbundle-f-sys.md) | 跨应用更新卡片，使用Promise异步回调。 |
<!--DelEnd-->
