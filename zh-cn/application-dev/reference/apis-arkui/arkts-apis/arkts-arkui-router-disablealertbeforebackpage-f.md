# disableAlertBeforeBackPage

## disableAlertBeforeBackPage

```TypeScript
function disableAlertBeforeBackPage(): void
```

禁用页面返回询问对话框。适用于用户已完成保存操作可以安全返回、页面状态切换后不再需要返回确认、需要动态控制返回行为等场景。与showAlertBeforeBackPage()方法成对使用：调用showAlertBeforeBackPage()开启对话框后，可在适当时机调用本方法关闭对话框。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [hideAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#hideAlertBeforeBackPage)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [hideAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#hideAlertBeforeBackPage)

<!--Device-router-function disableAlertBeforeBackPage(): void--><!--Device-router-function disableAlertBeforeBackPage(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

```TypeScript
import { router } from '@kit.ArkUI';

router.disableAlertBeforeBackPage();
```

