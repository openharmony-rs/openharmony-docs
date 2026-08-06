# ScrollDirectionalLockType

Enum defining the scope of directional lock behavior in the WebView, used with \_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare enum ScrollDirectionalLockType--><!--Device-unnamed-export declare enum ScrollDirectionalLockType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ALL

```TypeScript
ALL = 0
```

Applies directional lock across all scroll contexts. This includes both nested and flat scroll scenarios.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollDirectionalLockType-ALL = 0--><!--Device-ScrollDirectionalLockType-ALL = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NESTED_SCROLL

```TypeScript
NESTED_SCROLL = 1
```

Applies directional lock only within nested scroll scenarios. This is the default behavior in ArkWeb to improve UX in complex scroll hierarchies.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollDirectionalLockType-NESTED_SCROLL = 1--><!--Device-ScrollDirectionalLockType-NESTED_SCROLL = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

