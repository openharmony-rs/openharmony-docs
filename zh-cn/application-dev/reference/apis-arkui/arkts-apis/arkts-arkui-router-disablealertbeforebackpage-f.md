# disableAlertBeforeBackPage

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="disablealertbeforebackpage"></a>
## disableAlertBeforeBackPage

```TypeScript
function disableAlertBeforeBackPage(): void
```

禁用页面返回询问对话框。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [hideAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#hidealertbeforebackpage-1)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [hideAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#hidealertbeforebackpage-1)

<!--Device-router-function disableAlertBeforeBackPage(): void--><!--Device-router-function disableAlertBeforeBackPage(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```TypeScript
import { router } from '@kit.ArkUI';

router.disableAlertBeforeBackPage();

```

