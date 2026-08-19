# NestedScrollOptionsExt

用于设置Web组件嵌套滚动规则，支持上下左右四个方向的滚动选项。

**起始版本：** 14

<!--Device-unnamed-declare interface NestedScrollOptionsExt--><!--Device-unnamed-declare interface NestedScrollOptionsExt-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## scrollDown

```TypeScript
scrollDown?: NestedScrollMode
```

可滚动组件往下滚动时的嵌套滚动选项。 默认值：NestedScrollMode.SELF_FIRST。

**类型：** NestedScrollMode

**起始版本：** 14

<!--Device-NestedScrollOptionsExt-scrollDown?: NestedScrollMode--><!--Device-NestedScrollOptionsExt-scrollDown?: NestedScrollMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## scrollLeft

```TypeScript
scrollLeft?: NestedScrollMode
```

可滚动组件往左滚动时的嵌套滚动选项。 默认值：NestedScrollMode.SELF_FIRST。

**类型：** NestedScrollMode

**起始版本：** 14

<!--Device-NestedScrollOptionsExt-scrollLeft?: NestedScrollMode--><!--Device-NestedScrollOptionsExt-scrollLeft?: NestedScrollMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## scrollRight

```TypeScript
scrollRight?: NestedScrollMode
```

可滚动组件往右滚动时的嵌套滚动选项。 默认值：NestedScrollMode.SELF_FIRST。

**类型：** NestedScrollMode

**起始版本：** 14

<!--Device-NestedScrollOptionsExt-scrollRight?: NestedScrollMode--><!--Device-NestedScrollOptionsExt-scrollRight?: NestedScrollMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## scrollUp

```TypeScript
scrollUp?: NestedScrollMode
```

可滚动组件往上滚动时的嵌套滚动选项。 默认值：NestedScrollMode.SELF_FIRST。

**类型：** NestedScrollMode

**起始版本：** 14

<!--Device-NestedScrollOptionsExt-scrollUp?: NestedScrollMode--><!--Device-NestedScrollOptionsExt-scrollUp?: NestedScrollMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

