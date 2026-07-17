# WebBlanklessErrorCode

无白屏加载的异常错误码。

**起始版本：** 20

<!--Device-webview-enum WebBlanklessErrorCode--><!--Device-webview-enum WebBlanklessErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

成功。

**起始版本：** 20

<!--Device-WebBlanklessErrorCode-SUCCESS = 0--><!--Device-WebBlanklessErrorCode-SUCCESS = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_UNKNOWN

```TypeScript
ERR_UNKNOWN = -1
```

未知错误，内部状态错误等。

**起始版本：** 20

<!--Device-WebBlanklessErrorCode-ERR_UNKNOWN = -1--><!--Device-WebBlanklessErrorCode-ERR_UNKNOWN = -1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_INVALID_PARAM

```TypeScript
ERR_INVALID_PARAM = -2
```

参数不合法。

**起始版本：** 20

<!--Device-WebBlanklessErrorCode-ERR_INVALID_PARAM = -2--><!--Device-WebBlanklessErrorCode-ERR_INVALID_PARAM = -2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_CONTROLLER_NOT_INITED

```TypeScript
ERR_CONTROLLER_NOT_INITED = -3
```

WebViewController未绑定组件。

**起始版本：** 20

<!--Device-WebBlanklessErrorCode-ERR_CONTROLLER_NOT_INITED = -3--><!--Device-WebBlanklessErrorCode-ERR_CONTROLLER_NOT_INITED = -3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_KEY_NOT_MATCH

```TypeScript
ERR_KEY_NOT_MATCH = -4
```

未匹配到key值，对于[setBlanklessLoadingWithKey](arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithkey-1)需与[getBlanklessInfoWithKey](arkts-arkweb-webview-webviewcontroller-c.md#getblanklessinfowithkey-1)配套使用并且key值一致，否则返回该错误码。

**起始版本：** 20

<!--Device-WebBlanklessErrorCode-ERR_KEY_NOT_MATCH = -4--><!--Device-WebBlanklessErrorCode-ERR_KEY_NOT_MATCH = -4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_SIGNIFICANT_CHANGE

```TypeScript
ERR_SIGNIFICANT_CHANGE = -5
```

当相似度较低时，系统会判定为跳变太大，[setBlanklessLoadingWithKey](arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithkey-1)接口不会成功启用插帧。

**起始版本：** 20

<!--Device-WebBlanklessErrorCode-ERR_SIGNIFICANT_CHANGE = -5--><!--Device-WebBlanklessErrorCode-ERR_SIGNIFICANT_CHANGE = -5-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_DURATION_OUT_OF_RANGE

```TypeScript
ERR_DURATION_OUT_OF_RANGE = -6
```

在[BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md)设置的历史帧失效时间超出范围。

此接口仅可在Stage模型下使用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebBlanklessErrorCode-ERR_DURATION_OUT_OF_RANGE = -6--><!--Device-WebBlanklessErrorCode-ERR_DURATION_OUT_OF_RANGE = -6-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERR_EXPIRATION_TIME_OUT_OF_RANGE

```TypeScript
ERR_EXPIRATION_TIME_OUT_OF_RANGE = -7
```

在[BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md)设置的历史帧失效时间超出范围。

此接口仅可在Stage模型下使用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebBlanklessErrorCode-ERR_EXPIRATION_TIME_OUT_OF_RANGE = -7--><!--Device-WebBlanklessErrorCode-ERR_EXPIRATION_TIME_OUT_OF_RANGE = -7-End-->

**系统能力：** SystemCapability.Web.Webview.Core

