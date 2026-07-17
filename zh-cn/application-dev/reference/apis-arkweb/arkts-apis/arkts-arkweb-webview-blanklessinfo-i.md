# BlanklessInfo

页面首屏加载预测信息，主要包括首屏相似度预测值，首屏加载耗时预测值，预测错误码，应用需根据此信息来决策是否启用无白屏加载插帧方案。

**起始版本：** 20

<!--Device-webview-interface BlanklessInfo--><!--Device-webview-interface BlanklessInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## errCode

```TypeScript
errCode: WebBlanklessErrorCode
```

无白屏加载的异常错误码，见[WebBlanklessErrorCode](arkts-arkweb-webview-webblanklesserrorcode-e.md)定义。

**类型：** WebBlanklessErrorCode

**起始版本：** 20

<!--Device-BlanklessInfo-errCode: WebBlanklessErrorCode--><!--Device-BlanklessInfo-errCode: WebBlanklessErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## loadingTime

```TypeScript
loadingTime: number
```

根据历史加载首屏耗时预测本次加载耗时，单位ms，取值范围需大于0。

**类型：** number

**起始版本：** 20

<!--Device-BlanklessInfo-loadingTime: number--><!--Device-BlanklessInfo-loadingTime: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## similarity

```TypeScript
similarity: number
```

首屏相似度，根据历史加载首屏内容计算相似度，范围为[0, 1.0]，1.0表示完全一致，数值越接近1，相似度越高。该值存在滞后性，本地加载的相似性将在下次加载时才可反映。建议当相似度较低时，应用不启用无白屏加载插帧方案。

**类型：** number

**起始版本：** 20

<!--Device-BlanklessInfo-similarity: number--><!--Device-BlanklessInfo-similarity: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

