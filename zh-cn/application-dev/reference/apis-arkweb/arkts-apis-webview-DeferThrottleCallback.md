# Interface (DeferThrottleCallback)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @chenguanhao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

`DeferThrottleCallback`是[NavigationThrottle](./arkts-apis-webview-NavigationThrottle.md)回调返回DEFER后使用的异步决策句柄，作为四阶段回调的第二个参数传入。回调返回DEFER时导航挂起，应用可在任意时机调用[proceed()](#proceed)恢复导航或[cancel()](#cancel)取消导航，适用于弹窗确认、云端校验等长耗时决策场景。

> **说明：**
>
> - 仅回调返回DEFER后调用有效；未处于DEFER状态时调用被安全忽略，不抛出异常。
>
> - 同一DeferThrottleCallback仅首次调用生效，后续调用被安全忽略。
>
> - DEFER无内置超时，导航持续挂起直至应用调用proceed()/cancel()或Web组件销毁。
>
> - Web组件销毁后句柄失效，调用被安全忽略，不会产生崩溃。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 26.1.0

## proceed

proceed(): void

恢复被挂起的导航。恢复后导航从挂起点继续，最终结果与回调同步返回PROCEED一致。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 26.1.0

## cancel

cancel(): void

取消被挂起的导航。取消后本次导航终止，页面保持当前文档，最终结果与回调同步返回CANCEL一致。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 26.1.0
