# UpdateFormsConfigCallback（系统接口）

```TypeScript
type UpdateFormsConfigCallback = (configInfo: Array<FormCustomConfig>) => void
```

卡片配置更新回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configInfo | Array&lt;[FormCustomConfig](arkts-form-forminfo-formcustomconfig-i-sys.md)&gt; | 是 | 卡片配置信息列表。 |

**示例**

```TypeScript
import { formInfo } from '@kit.FormKit';

let updateFormsConfigCallback: formInfo.UpdateFormsConfigCallback =
  (configInfo: Array<formInfo.FormCustomConfig>): void => {
    console.info('update forms config callback, config count: ' + configInfo.length);
  };
```
