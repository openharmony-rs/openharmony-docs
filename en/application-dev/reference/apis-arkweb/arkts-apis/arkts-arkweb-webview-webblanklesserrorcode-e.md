# WebBlanklessErrorCode

Enumerates the error codes of the blankless loading.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

Operation successful.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## ERR_UNKNOWN

```TypeScript
ERR_UNKNOWN = -1
```

Unknown error or internal status error.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## ERR_INVALID_PARAM

```TypeScript
ERR_INVALID_PARAM = -2
```

Invalid parameter.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## ERR_CONTROLLER_NOT_INITED

```TypeScript
ERR_CONTROLLER_NOT_INITED = -3
```

**WebViewController** is not bound to any component.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## ERR_KEY_NOT_MATCH

```TypeScript
ERR_KEY_NOT_MATCH = -4
```

No key value is matched. [setBlanklessLoadingWithKey](arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithkey) must be used with [getBlanklessInfoWithKey](arkts-arkweb-webview-webviewcontroller-c.md#getblanklessinfowithkey) and their key values must be the same. Otherwise, this error code is returned.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## ERR_SIGNIFICANT_CHANGE

```TypeScript
ERR_SIGNIFICANT_CHANGE = -5
```

The similarity is low, and the system determines that the scene change is too large. As a result, the [setBlanklessLoadingWithKey](arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithkey) API does not enable frame interpolation.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## ERR_DURATION_OUT_OF_RANGE

```TypeScript
ERR_DURATION_OUT_OF_RANGE = -6
```

The frame interpolation duration set in [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md) is out of range.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## ERR_EXPIRATION_TIME_OUT_OF_RANGE

```TypeScript
ERR_EXPIRATION_TIME_OUT_OF_RANGE = -7
```

The historical frame expiration time set in [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md) is out of range.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
