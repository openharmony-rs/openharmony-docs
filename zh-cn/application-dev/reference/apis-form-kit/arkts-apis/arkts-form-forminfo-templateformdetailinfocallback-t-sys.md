# TemplateFormDetailInfoCallback（系统接口）

```TypeScript
type TemplateFormDetailInfoCallback = (info: Array<TemplateFormDetailInfo>) => void
```

模板卡真实卡片信息回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | Array&lt;[TemplateFormDetailInfo](arkts-form-forminfo-templateformdetailinfo-i-sys.md)&gt; | 是 | 模板卡真实卡片信息。 |

**示例**

```TypeScript
import { formInfo } from '@kit.FormKit';

let templateFormDetailInfoCallback: formInfo.TemplateFormDetailInfoCallback =
  (info: Array<formInfo.TemplateFormDetailInfo>): void => {
    console.info('template form detail info callback success.');
  };
```
